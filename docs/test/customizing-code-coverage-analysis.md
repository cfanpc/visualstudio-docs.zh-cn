---
title: 自定义代码覆盖率分析
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 8749cd7757796a1b716b1ac9db086d3155f94694
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965541"
---
# <a name="customize-code-coverage-analysis"></a>自定义代码覆盖率分析

默认情况下，代码覆盖率将分析单元测试过程中加载的所有解决方案程序集。 建议使用此默认行为，因为它大多数时间很有用。 有关详细信息，请参阅[使用代码覆盖率确定正在测试的代码数量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)。

若要从代码覆盖率结果中排除测试代码，仅包括应用程序代码，请将 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 属性添加到测试类。

若要包含不属于解决方案的程序集，请获取这些程序集的 .pdb 文件并将其复制到与程序集 .dll 文件相同的文件夹。

## <a name="run-settings-file"></a>运行设置文件

[运行设置文件](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)是由单元测试工具使用的配置文件。 在 .runsettings 文件中指定高级代码覆盖率设置。

若要自定义代码覆盖率，请执行以下步骤：

1. 将运行设置文件添加到解决方案中。 在“解决方案资源管理器”的解决方案快捷菜单上，依次选择“添加” > “新建项”和“XML 文件”。 保存带有类似于 CodeCoverage.runsettings 的名称的文件。

1. 添加本文结尾处示例文件中的内容，然后按需进行自定义，如以下章节所述。

1. 若要选择运行设置文件，在“测试”菜单上，选择“测试设置” > “选择测试设置文件”。 若要指定运行设置文件以从命令行或在生成工作流中运行测试，请参阅[使用 .runsettings 文件配置单元测试](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file)。

   选择“分析代码覆盖率”时，会从运行设置文件读取配置信息。

   > [!TIP]
   > 在运行测试或更新代码时，之前的代码覆盖率结果和代码着色不会自动隐藏。

若要禁用和启用自定义设置，请依次选择“测试”和“测试设置” > 菜单，然后取消选择或选择文件。

![包含自定义设置文件的测试设置菜单](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>指定符号搜索路径

代码覆盖率需要程序集的符号文件（.pdb 文件）。 对于解决方案生成的程序集，符号文件通常与二进制文件一起出现，且代码覆盖率将自动工作。 但在某些情况下，你可能需要在你的代码覆盖率分析中包含引用的程序集。 在这种情况下，.pdb 文件可能不会与二进制文件相邻，但可在 .runsettings 文件中指定符号搜索路径。

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> 符号解析可能很耗时，尤其是在使用包含大量程序集的远程文件位置时。 因此，请考虑将 .pdb 文件复制到与二进制文件（.dll 和 .exe）相同的本地位置。

### <a name="exclude-and-include"></a>排除和包含

你可以从代码覆盖率分析中排除指定的程序集。 例如:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

或者，你也可以指定应包含的程序集。 此方法的一个缺点是，当你将多个程序集添加到解决方案时，必须记住将它们添加到列表：

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

如果“Include”为空，那么代码覆盖率会处理已加载且能找到 .pdb 文件的所有程序集。 代码覆盖率不包括与“Exclude”列表中子句匹配的项。

先处理“Include”，再处理“Exclude”。

### <a name="regular-expressions"></a>正则表达式

包括和排除节点使用正则表达式。 有关详细信息，请参阅[在 Visual Studio 中使用正则表达式](../ide/using-regular-expressions-in-visual-studio.md)。 正则表达式与通配符不同。 具体而言：

- .\\* 与包含任意字符的字符串匹配

- **\\.** 与句点“.”匹配

- **\\(   \\)** 与括号“(  )”匹配

- **\\\\** 与文件路径分隔符“\\”匹配

- **^** 与字符串的开头匹配

- **$** 与字符串的结尾匹配

所有匹配项都不区分大小写。

例如:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

> [!WARNING]
> 如果正则表达式中存在错误（如存在未转义或不匹配的括号），则不会运行代码覆盖率分析。

### <a name="other-ways-to-include-or-exclude-elements"></a>包括或排除元素的其他方法

- **ModulePath** - 匹配程序集文件路径指定的程序集。

- **CompanyName** - 按“公司”属性匹配程序集。

- **PublicKeyToken** - 按公钥标记匹配签名的程序集。

- **Source** - 按在其中定义元素的源文件路径名称匹配元素。

- **Attribute** - 匹配附加特定属性的元素。 指定属性的全名并在名称结尾处包括“Attribute”。

- **Function** - 按完全限定名匹配过程、函数或方法。 若要匹配函数名称，则正则表达式必须与函数的完全限定名匹配，包括命名空间、类名、方法名称和参数列表。 例如:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

   ```xml
   <Functions>
     <Include>
       <!-- Include methods in the Fabrikam namespace: -->
       <Function>^Fabrikam\..*</Function>
       <!-- Include all methods named EqualTo: -->
       <Function>.*\.EqualTo\(.*</Function>
     </Include>
     <Exclude>
       <!-- Exclude methods in a class or namespace named UnitTest: -->
       <Function>.*\.UnitTest\..*</Function>
     </Exclude>
   </Functions>
   ```

## <a name="sample-runsettings-file"></a>示例 .runsettings 文件

复制此代码并对其进行编辑以满足需求。

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>请参阅

- [使用运行设置文件配置单元测试](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [使用代码覆盖率确定所测试的代码量](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [单元测试代码](../test/unit-test-your-code.md)