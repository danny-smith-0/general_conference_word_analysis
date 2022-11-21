# Regex to santize inputs

## Punctuation

### - Corner Case 1

Remove periods and/or end quotes immediately followed by a number or letter (footnotes)

``` txt
   find: (”|\.)+\w+
replace: nothing            e.g.  serve.”8 => serve
```

There might be issues here with type of quote 😑 " vs ”

### - Corner Case 2

Remove commas within numbers

``` txt
   find: (\d)(,)(\d)
replace: $1$3               e.g.  30,000 => 30000
```

### - All the remaining punction

Replace any remaining punction with a space

``` txt
   find: [[:punct:]]+
replace: <a_space>
```

---

## White space

Replace line breaks with a space

``` txt
   find: \r\n
replace: <1_space>
```

Replace multiple spaces with a single space

``` txt
   find: <1_space>+
replace: <1_space>
```
