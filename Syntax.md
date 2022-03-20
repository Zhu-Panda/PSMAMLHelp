# Command Syntax

## 1. Main Container

```xml

<command:syntaxItem> <!-- main container -->
    <!-- syntax for this parameter set goes here -->
</command:syntaxItem>

```

## 2. Basic Syntax Structure

```xml

<maml:name><!--command name (verb-noun) here --></maml:name>
<command:parameter> <!-- with attrs -->
    <!-- help for parameter 1 -->
</command:parameter>
<command:parameter> <!-- with attrs -->
    <!-- help for parameter 2 -->
</command:parameter>
<!-- and so on... -->

```

## 3. Parameter Container Structure

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

## 4. Parameter Container Attributes

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

### 4.1. Required Attribute <a name="required"></a>

Just a regular boolean:

```xml

<command:parameter required="true">
</command:parameter>

```

### 4.2. Position Attribute <a name="position"></a>

A number if it is positional, or ```named``` if it is named:

```xml

<command:parameter position="0">
</command:parameter>

```

### 4.3. Pipeline Input Attribute <a name="pipelineInput"></a>

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

### 4.4. Globbing Attribute <a name="globbing"></a>

Just a regular boolean:

```xml

<command:parameter globbing="true">
</command:parameter>

```

### 4.5. Required Attribute (ParameterValue)

Just a regular boolean:

```xml

<command:parameterValue required="true">
</command:parameterValue>

```

## 5. Constructing The Syntax Diagram

First start with the command name:

```

SYNTAX
    Get-RecordFromDB

```

Then list all parameters from all parameter sets:

```xml

SYNTAX
    Get-RecordFromDB -Name -Type -Format <!-- get the default parameter set first -->
    Get-RecordFromDB -Id -Type -Format
    <!-- order parameters in each set by category in this order: positional, unique, common -->
    <!-- then order them in each category as you intended -->
    <!-- don't add common parameters as Get-Help will add them for you -->

```

Add the parameter values:

```xml

SYNTAX
    Get-RecordFromDB -Name System.String -Type Basic Detailed -Format
    Get-RecordFromDB -Id System.Int32 -Type Basic Detailed -Format
    <!-- parameter values are represented by their .NET types -->
    <!-- except for enums, where all possible values are listed -->
    <!-- and switches, which have no value -->
    <!-- types can be abbreviated as long as their meaning is clear, e.g. System.String to string, and System.Int32 to int -->

```

Add angle brackets around placeholders:

```

SYNTAX
    Get-RecordFromDB -Name <System.String> -Type Basic Detailed -Format
    Get-RecordFromDB -Id <System.Int32> -Type Basic Detailed -Format

```

Enclose optional parameters and optional parameter names (for positional parameters) in square brackets:

```

SYNTAX
    Get-RecordFromDB [[-Name] <System.String>] [-Type Basic Detailed] [-Format]
    Get-RecordFromDB -Id <System.Int32> [-Type Basic Detailed] [-Format]

```