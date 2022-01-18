# Whats New IN PHP 8

### Named Arguments

Arguments are order-independent and self-documented.

```other
htmlspecialchars($string, double_encode: false);
```

Attributes

Instead of PHPDoc annotations, you can now use structured metadata with PHP's native syntax.

```other
#[Route("/api/posts/{id}", methods: ["GET"])]
```

### Constructor Property Promotion

```other
class Point {
  public function __construct(
    public float $x = 0.0,
    public float $y = 0.0,
    public float $z = 0.0,
  ) {}
}

is Equivalent to 

class Point {
  public float $x;
  public float $y;
  public float $z;

  public function __construct(
    float $x = 0.0,
    float $y = 0.0,
    float $z = 0.0
  ) {
    $this->x = $x;
    $this->y = $y;
    $this->z = $z;
  }
}
```

### Union Types

```other
class Number {
  public function __construct(
    private int|float $number
  ) {}
}

new Number('NaN'); // TypeError
```

### Match Expression

The new match is similar to switch and has the following features:

- Match is an expression, meaning its result can be stored in a variable or returned.
- Match branches only support single-line expressions and do not need a break; statement.
- Match does strict comparisons.

```other
echo match (8.0) {
  '8.0' => "Oh no!",
  8.0 => "This is what I expected",
};
//> This is what I expected
```

### Nullsafe Operator

```other
$country = $session?->user?->getAddress()?->country;
```


