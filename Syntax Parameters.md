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

<pre><code>

<a href="#required">Required?</a>                    false
<a href="#position">Position?</a>                    0
Default value                None
Accept pipeline input?       False
Accept wildcard characters?  false

</code></pre>

### 2.1. Required Attribute <a name="required"></a>

Just a regular boolean:

```xml

<command:parameter required="true">
</command:parameter>

```

### 2.2. Position Attribute <a name="position"></a>

A number if it is positional, or ```named``` if it is named:

```xml

<command:parameter position="0">
</command:parameter>

```