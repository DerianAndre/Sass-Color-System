# Sass-Color-System
A simple color system made with Sass using CSS variables
Using HSLA and variables you can achieve a simple effective color system that can be more complex to your needs.

```
  $color: hsl(0, 50%, 50%);
  --color-alpha: 1;
  --color-h:  #{color.hue($color)};
  --color-s:  #{color.saturation($color)};
  --color-l:  #{color.lightness($color)};
  --color-hsl: 
    hsl(
      var(--color-hue,        var(--#{$name}-h)),
      var(--color-saturation, var(--#{$name}-s)),
      var(--color-lightness,  var(--#{$name}-l))
    );
  --color-hsla: 
    hsla(
      var(--color-hue,        var(--#{$name}-h)),
      var(--color-saturation, var(--#{$name}-s)),
      var(--color-lightness,  var(--#{$name}-l)),
      var(--color-alpha,      var(--alpha-color))
    );
```

Using `sass:color` we can convert any color into hsl, with that we can separate into css variables and we can modify them to our needs.

If we want to make it slightly more transparent then we only need to change a variable instead of rewrting a property:
```
  .div {
    background-color: hsla(0, 50%, 50%, 1);
  }
  .div:hover {
    background-color: hsla(0, 80%, 40%, 0.5);
  }
```

With my color system:

```
  .better-div {
    backgorund-color: var(--color-hsla);
  }
  .better-div:hover {
    --color-saturation: 80%;
    --color-lightness : 40%;
    --color-alpha     : 0.50;
  }
```

The best thing is that we can do this for hue, saturation, lightness and alpha values to every single color.

With this aproach we can save really a lot of time and rewrites (long term). 
This aproach seems like more coding, this is probably not the best way when you are writing a simple web/app but for a larger system this can be really helpful.
Also if you use a post-processor code can have a smaller foot-print.