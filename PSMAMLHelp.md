# PowerShell MAML Help

## 1. XML Schema And HelpItems

```xml

<?xml version="1.0" encoding="utf-8"?> <!-- XML schema -->
<helpItems schema="maml" xmlns="http://msh"> <!-- main container -->
    <!-- everything inside... -->
</helpItems>

```

## 2. Command

```xml

<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10" xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10" xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10" xmlns:MSHelp="http://msdn.microsoft.com/mshelp"> <!-- command container with a bunch of schemas -->
    <!-- everything inside... -->
</command:command>

```

## 3. Command Name, Synopsis And Description

```xml

<command:details>
    <command:name><!--command name (verb-noun) here --></command:name>
    <command:verb><!--command verb here --></command:verb>
    <command:noun><!--command noun here --></command:noun>
    <maml:description>
        <maml:para><!-- synopsis here --></maml:para>
    </maml:description>
</command:details>
<maml:description>
    <maml:para><!-- description here --></maml:para>
</maml:description>

```

## 4. Command Syntax

```xml

<command:syntax>
    <command:syntaxItem>
        <!-- parameter set 1 (default parameter set) parameters go here -->
    </command:syntaxItem>
    <command:syntaxItem>
        <!-- parameter set 2 parameters go here -->
    </command:syntaxItem>
    <!-- and so on... -->
</command:syntax>

```

For more, check out [Syntax.md](./Syntax.md).