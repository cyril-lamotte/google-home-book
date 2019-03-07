# Mixins

### Layout

#### Clearfix

```sass
@include clearfix;
```

#### Absolute positionning

Add absolute positioning, full-size of first relative parent.

```sass
@include absolute-full;
```


#### Spread block to window's edges.

```sass
@include full-width;
```


#### Maintain iframes/objects ratio.

```sass
@include ratio-wrap(9/16);
```




### Responsive

```sass
// Add a "max-width" media querie.
@include mq-to('sm');

// Add a "min-width" media querie.
@include mq-from('md');

// Add a "min-width" & "max-width" media querie.
@include mq-from-to('sm', 'md');

// Add a "max-height" media querie for vertical RWD.
@include mq-vert-to('sm');
```



### Content

#### Hide text (for screen readers)

```sass
@include hide;
```


#### Text wrap

The margin-top of the first element & the margin-bottom of the last one are
removed.

```sass
@include text-wrap;
```


#### Text overflow

Add '...' after text  (1 line only).

```sass
@include text-overflow;
```










### FX

#### Définir un effet de survol (et/ou focus).

```sass
@include hover {};
@include focus {};
```


#### Soulignement des liens

```sass
@include underline;
@include underline('inv');
```


