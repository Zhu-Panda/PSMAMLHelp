# Syntax Parameters

## 1. Parameter Container Structure

<a name="defaultValue">

```xml

<command:parameter> <!-- with attrs -->
    <maml:name><!-- parameter name --></maml:name>
    <maml:description>
        <maml:para><!-- parameter description --></maml:para>
        </maml:description>
        <command:parameterValue> <!-- with attrs -->
            <!-- parameter's .NET type -->
        </command:parameterValue>
        <dev:type>
            <maml:name><!-- parameter's .NET type --></maml:name>
            <maml:uri />
        </dev:type>
    <dev:defaultValue><!-- parameter's default value --></dev:defaultValue>
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
<a href="#defaultValue">Default value</a>                None
<a href="#pipelineInput">Accept pipeline input?</a>       False
<a href="#globbing">Accept wildcard characters?</a>  false

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

### 2.3. Pipeline Input Attribute <a name="pipelineInput"></a>

This attribute can be set to 1 of the following 4 values:

```xml

true (ByValue) <!-- pipe by value -->
true (ByPropertyName) <!-- pipe by property name -->
true (ByValue, ByPropertyName) <!-- pipe by both -->
false <!-- cannot pipe-->

```

Example:

```xml

<command:parameter pipelineInput="false">
</command:parameter>

```

### 2.4. Globbing Attribute <a name="globbing"></a>

Just a regular boolean:

```xml

<command:parameter globbing="true">
</command:parameter>

```

### 2.5. Required Attribute (ParameterValue)

Just a regular boolean:

```xml

<command:parameterValue required="true">
</command:parameterValue>

```