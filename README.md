# Semicolon

```c
printf("%d %d %d %d %d %d\n",  1,  a,  b + c,  d++,  e = 5,  f()) ;

d++ ;
e = 5 ;
f() ;

// warning: statement has no effect [-Wunused-value]
"%d %d %d %d %d %d\n" ;
1 ;
a ;
b + c ;
```

## Expression statement

```c
expression-statement:
    expression ;
```

> The *expression* in an *expression statement* is *evaluated* as a *void expression* for its *side effects*.

## Side effects

| Operator | Side effect | Value | Example |
| -------- | ----------- | ----- | ------- |
| `v = e` | evaluate `e`, assign to `v` | new value of `v` | `i = j = 0 ;`
| `i++` | increment `i` | old value of `i` | `int x = a[i++] ;`
| `i--` | decrement `i` | old value of `i` | `while (i --> 0) printf("%d\n", i) ;`
| `++i` | increment `i` | new value of `i` | `return ++i ;`
| `--i` | decrement `i` | new value of `i` | `if (--i < 0) i = 99 ;`
| `a, b` | those of `a`, those of `b` | value of `b` | `for (i = 0, j = n - 1 ; i < j ; ++i, --j)` |
| `f(x)` | those of `x`, run `f` | `return value ;` | `guess_me = random(0, prompt("max? ") + 1) ;` |

## Full expression

> A *full expression* is an expression that is not part of another expression.
> Each of the following is a full expression:
> 
> - an initializer
> - the expression in an expression statement
> - the controlling expression of a selection statement (`if` or `switch`)
> - the controlling expression of a `while` or `do` statement
> - each of the three expressions of a `for` statement
> - the expression in a `return` statement

## Spot the bugs

```c
void bugs()
{
    int i ;
    for (i == 0 ; i = 10 ; i + 1)
    {
        sqrt(81) ;
    }
}

unsigned long generate_unique_id()
{
    static unsigned long id ;
    ASSERT(++id > 0) ;
    return id;
}
```
