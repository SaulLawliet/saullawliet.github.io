---
layout: post
title: Java 工厂方法模式 进阶
categories: java
comments: true
share: false
image:
  feature:

modified:
---
> 直接上代码

目录结构:

~~~
.
├── product
│   ├── my
│   │   └── MyProduct.java
│   ├── your
│   │   └── YourProduct.java
│   ├── AbstractProduct.java
│   └── Product.java
├── util
│   └── RTSI.java
└── Main.java
~~~

代码:

~~~ java
// ProductType.java
public enum ProductType {
	MY, YOUR,
}

// Product.java
public interface Product {
	void sayHi();
	ProductType getType();
}

// AbstractProduct.java
public abstract class AbstractProduct implements Product {
	@Override
	public void sayHi() {
		System.out.println("Hi, from " + this.getClass().getSimpleName());
	}
}

// MyProduct.java
public class MyProduct extends AbstractProduct {
	@Override
	public ProductType getType() {
		return ProductType.MY;
	}
}

// YourProduct.java
public class YourProduct extends AbstractProduct {
	@Override
	public ProductType getType() {
		return ProductType.YOUR;
	}
}

// Test.java
public class Test {

	// 传统工厂方法的弊端, 每次新增类型的时候, 都要修改一下这个方法
	private static void oldVersion(ProductType type) {
		switch (type) {
			case MY:
				new MyProduct().sayHi();
				break;
			case YOUR:
				new YourProduct().sayHi();
				break;
		}
	}

	private static void newVersion(Map<ProductType, Class<AbstractProduct>> map, ProductType type) throws Exception{
		Class<AbstractProduct> c = map.get(type);
		if (c != null) {
			c.newInstance().sayHi();
		}
	}

	public static void main(String []args) throws Exception {
		System.out.println("======= old =======");
		for (ProductType type : ProductType.values()) {
			oldVersion(type);
		}

		System.out.println("======= new =======");
		Map<ProductType, Class<AbstractProduct>> map = new HashMap<ProductType, Class<AbstractProduct>>();
		Set<Class<AbstractProduct>> set = RTSI.findClass(AbstractProduct.class);
		for (Class<AbstractProduct> c : set) {
			map.put(c.newInstance().getType(), c);
		}

		for (ProductType type : ProductType.values()) {
			newVersion(map, type);
		}
	}
}
~~~

输出:

~~~
======= old =======
Hi, from MyProduct
Hi, from YourProduct

======= new =======
Hi, from MyProduct
Hi, from YourProduct
~~~

-----
RTSI.java

{% gist SaulLawliet/bb5e3d2e11df5b5cb0a3f865523b1d84 %}
