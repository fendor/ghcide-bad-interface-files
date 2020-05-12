# Minimal reproducible example from https://github.com/mpickering/ghcide/pull/29

Reproduce:

* Install ghcide from https://github.com/mpickering/ghcide
* Open `foo/Foo.hs` and hover on some Identifier
* Open `bar/Bar.hs` and hover on some Identifier
* In foo/Foo.hs, there should be an error such as:
  ```
  foo\Foo.hs:8:7: error:
    • Couldn't match expected type ‘SomeId’
                  with actual type ‘bar-0.1.0.0:Bar.SomeId’
      NB: ‘bar-0.1.0.0:Bar.SomeId’
            is defined in ‘Bar’ in package ‘bar-0.1.0.0’
          ‘SomeId’ is defined at
            Bar.hs:3:1-40
    • In the expression: produceId
      In an equation for ‘foo’: foo = produceId
  ```

The error is fixed if you open `glue/Glue.hs`.