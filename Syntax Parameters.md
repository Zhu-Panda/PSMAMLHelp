# Syntax Parameters

## 1. Parameter Container

```xml

<command:parameter> <!-- with attrs -->
    <!-- help for this parameter -->
</command:parameter>

```

## 2. Parameter Container Attributes

Normally when you use ```Get-Help```, you see something like this:

```

----- text above... -----

SYNTAX
    Verb-Noun [[-Parameter] <String>] [<CommonParameters>]


DESCRIPTION
    Description


PARAMETERS
    -Parameter <String>
        Parameter Description

        Required?                    false
        Position?                    0
        Default value                None
        Accept pipeline input?       False
        Accept wildcard characters?  false

----- text below... -----

```

What you need is this block:

```

Required?                    false
Position?                    0
Default value                None
Accept pipeline input?       False
Accept wildcard characters?  false

```