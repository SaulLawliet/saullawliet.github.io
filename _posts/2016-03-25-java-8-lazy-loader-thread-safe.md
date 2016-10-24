---
layout: post
title:  Java 8 中线程安全的延时加载
category: java
comments: true
share: false
image:
  feature:

modified:
---

没有见过的用法，做个记录。

> - [Lazy Loading](http://java-design-patterns.com/patterns/lazy-loading/) <br />
> - [Supplier](https://docs.oracle.com/javase/8/docs/api/java/util/function/Supplier.html)

~~~ java
...

public class Holder {
    private Supplier<Heavy> heavy = () -> createAndCacheHeavy();

    public Heavy getHeavy() {
        return heavy.get();
    }

    private synchronized Heavy createAndCacheHeavy() {

        class HeavyFactory implements Supplier<Heavy> {
            private final Heavy heavyInstance = new Heavy();
            @Override
            public Heavy get() {
                return heavyInstance;
            }
        }

        if (!HeavyFactory.class.isInstance(heavy)) {
            heavy = new HeavyFactory();
        }

        return heavy.get();
    }
}
~~~
