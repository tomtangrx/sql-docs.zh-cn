---
title: "分析非标准的文本文件格式 with the Script Component |Microsoft 文档"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- text file reading [Integration Services]
- Script component [Integration Services], non-standard text file formats
- transformations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: 1fda034d-09e4-4647-9a9f-e8d508c2cc8f
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c6bf6a70027da7804e2fdca998948d44c9a26097
ms.contentlocale: zh-cn
ms.lasthandoff: 09/26/2017

---
# <a name="parsing-non-standard-text-file-formats-with-the-script-component"></a>使用脚本组件分析非标准文本文件格式
  当源数据以非标准格式排列时，您可能会发现在一个脚本中合并所有分析逻辑要比将多个 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 转换链接在一起以实现相同结果更方便。  
  
 [示例 1： 分析行分隔记录](#example1)  
  
 [示例 2： 拆分父和子记录](#example2)  
  
> [!NOTE]  
>  如果希望创建可更方便地重用于多个数据流任务和多个包的组件，请考虑以此脚本组件示例中的代码为基础，创建自定义数据流组件。 有关详细信息，请参阅 [开发自定义数据流组件](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)。  
  
##  <a name="example1"></a>示例 1： 分析行分隔记录  
 本示例演示如何采用其中包含的每列数据显示在单独一行中的文本文件，并使用脚本组件对该文件进行分析，分析结果写入目标表。  
  
 有关如何将使用脚本组件配置为数据流中的数据转换的详细信息，请参阅[使用脚本组件创建同步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用脚本组件创建异步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。  
  
#### <a name="to-configure-this-script-component-example"></a>配置此脚本组件示例  
  
1.  创建并保存一个名为文本文件**rowdelimiteddata.txt**包含以下源数据：  
  
    ```  
    FirstName: Nancy  
    LastName: Davolio  
    Title: Sales Representative  
    City: Seattle  
    StateProvince: WA  
  
    FirstName: Andrew  
    LastName: Fuller  
    Title: Vice President, Sales  
    City: Tacoma  
    StateProvince: WA  
  
    FirstName: Steven  
    LastName: Buchanan  
    Title: Sales Manager  
    City: London  
    StateProvince:  
  
    ```  
  
2.  打开 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。  
  
3.  选择目标数据库，并打开新查询窗口。 在该查询窗口中，执行以下脚本以创建目标表：  
  
    ```  
    create table RowDelimitedData  
    (  
    FirstName varchar(32),  
    LastName varchar(32),  
    Title varchar(32),  
    City varchar(32),  
    StateProvince varchar(32)  
    )  
  
    ```  
  
4.  打开 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 并创建名为 ParseRowDelim.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
5.  向包中添加平面文件连接管理器，将其命名为 RowDelimitedData 并配置其连接到在前面步骤中创建的 rowdelimiteddata.txt 文件。  
  
6.  向包中添加 OLE DB 连接管理器，并配置其连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和在其中创建了目标表的数据库。  
  
7.  将数据流任务添加到包并单击**数据流**SSIS 设计器选项卡。  
  
8.  向数据流添加平面文件源，并将其配置为使用 RowDelimitedData 连接管理器。 上**列**页**平面文件源编辑器**，选择单个可用外部列。  
  
9. 向数据流添加脚本组件并将其配置为转换。 将平面文件源的输出连接到脚本组件。  
  
10. 双击要显示的脚本组件**脚本转换编辑器**。  
  
11. 上**输入列**页**脚本转换编辑器**，选择单个可用输入的列。  
  
12. 上**输入和输出**页**脚本转换编辑器**，选择输出 0 并设置其**SynchronousInputID**为 None。 创建 5 个输出列，所有 [DT_STR] 类型字符串的长度为 32：  
  
    -   FirstName  
  
    -   LastName  
  
    -   Title  
  
    -   City  
  
    -   StateProvince  
  
13. 上**脚本**页**脚本转换编辑器**，单击**编辑脚本**然后输入中所示的代码**ScriptMain**类该示例。 关闭脚本开发环境和**脚本转换编辑器**。  
  
14. 向数据流添加 SQL Server 目标。 将该目标配置为使用 OLE DB 连接管理器和 RowDelimitedData 表。 将脚本组件的输出连接到此目标。  
  
15. 运行包。 包运行完毕后，检查 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标表中的记录。  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Dim columnName As String  
    Dim columnValue As String  
  
    ' Check for an empty row.  
    If Row.Column0.Trim.Length > 0 Then  
        columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"))  
        ' Check for an empty value after the colon.  
        If Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd.Length > 1 Then  
            ' Extract the column value from after the colon and space.  
            columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2)  
            Select Case columnName  
                Case "FirstName"  
                    ' The FirstName value indicates a new record.  
                    Me.Output0Buffer.AddRow()  
                    Me.Output0Buffer.FirstName = columnValue  
                Case "LastName"  
                    Me.Output0Buffer.LastName = columnValue  
                Case "Title"  
                    Me.Output0Buffer.Title = columnValue  
                Case "City"  
                    Me.Output0Buffer.City = columnValue  
                Case "StateProvince"  
                    Me.Output0Buffer.StateProvince = columnValue  
            End Select  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
        string columnName;  
        string columnValue;  
  
        // Check for an empty row.  
        if (Row.Column0.Trim().Length > 0)  
        {  
            columnName = Row.Column0.Substring(0, Row.Column0.IndexOf(":"));  
            // Check for an empty value after the colon.  
            if (Row.Column0.Substring(Row.Column0.IndexOf(":")).TrimEnd().Length > 1)  
            // Extract the column value from after the colon and space.  
            {  
                columnValue = Row.Column0.Substring(Row.Column0.IndexOf(":") + 2);  
                switch (columnName)  
                {  
                    case "FirstName":  
                        // The FirstName value indicates a new record.  
                        this.Output0Buffer.AddRow();  
                        this.Output0Buffer.FirstName = columnValue;  
                        break;  
                    case "LastName":  
                        this.Output0Buffer.LastName = columnValue;  
                        break;  
                    case "Title":  
                        this.Output0Buffer.Title = columnValue;  
                        break;  
                    case "City":  
                        this.Output0Buffer.City = columnValue;  
                        break;  
                    case "StateProvince":  
                        this.Output0Buffer.StateProvince = columnValue;  
                        break;  
                }  
            }  
        }  
  
    }  
```  
  
##  <a name="example2"></a>示例 2： 拆分父和子记录  
 本示例演示如何采用格式为父记录行的前面有一个分隔符行，父记录行后跟任意个子记录行的文本文件，并使用脚本组件对其进行分析，分析结果写入已适当规范化的父目标表和子目标表中。 这是一个简单的示例，它易于调整以适合每个父记录和子记录使用多行或多列的源文件，只要有办法识别每个记录的开始和结尾。  
  
> [!CAUTION]  
>  此示例仅供演示之用。 如果多次运行该示例，则会在目标表中插入重复的键值。  
  
 有关如何将使用脚本组件配置为数据流中的数据转换的详细信息，请参阅[使用脚本组件创建同步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)和[使用脚本组件创建异步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)。  
  
#### <a name="to-configure-this-script-component-example"></a>配置此脚本组件示例  
  
1.  创建并保存一个名为文本文件**parentchilddata.txt**包含以下源数据：  
  
    ```  
    **********  
    PARENT 1 DATA  
    child 1 data  
    child 2 data  
    child 3 data  
    child 4 data  
    **********  
    PARENT 2 DATA  
    child 5 data  
    child 6 data  
    child 7 data  
    child 8 data  
    **********  
  
    ```  
  
2.  打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 并连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。  
  
3.  选择目标数据库，并打开新查询窗口。 在查询窗口中，执行以下用于创建目标表的脚本：  
  
    ```  
    CREATE TABLE [dbo].[Parents]([ParentID] [int] NOT NULL,  
    [ParentRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Parents] PRIMARY KEY CLUSTERED   
    ([ParentID] ASC))  
    GO  
    CREATE TABLE [dbo].[Children]([ChildID] [int] NOT NULL,  
    [ParentID] [int] NOT NULL,  
    [ChildRecord] [varchar](32) NOT NULL,  
     CONSTRAINT [PK_Children] PRIMARY KEY CLUSTERED   
    ([ChildID] ASC))  
    GO  
    ALTER TABLE [dbo].[Children] ADD CONSTRAINT [FK_Children_Parents] FOREIGN KEY([ParentID])  
    REFERENCES [dbo].[Parents] ([ParentID])  
  
    ```  
  
4.  打开 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 并创建名为 SplitParentChild.dtsx 的新 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包。  
  
5.  向包中添加平面文件连接管理器，将其命名为 ParentChildData 并配置其连接到在前面步骤中创建的 parentchilddata.txt 文件。  
  
6.  向包中添加 OLE DB 连接管理器，并配置其连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例和在其中创建目标表的数据库。  
  
7.  将数据流任务添加到包并单击**数据流**SSIS 设计器选项卡。  
  
8.  向数据流添加平面文件源，并将其配置为使用 ParentChildData 连接管理器。 上**列**页**平面文件源编辑器**，选择单个可用外部列。  
  
9. 向数据流添加脚本组件并将其配置为转换。 将平面文件源的输出连接到脚本组件。  
  
10. 双击要显示的脚本组件**脚本转换编辑器**。  
  
11. 上**输入列**页**脚本转换编辑器**，选择单个可用输入的列。  
  
12. 上**输入和输出**页**脚本转换编辑器**、 选择输出 0，将它重命名为 ParentRecords，并设置其**SynchronousInputID**为 None。 创建 2 输出列：  
  
    -   ParentID（主键），类型为四字节有符号整数 [DT_I4]  
  
    -   ParentRecord，类型为长度为 32 的字符串 [DT_STR]。  
  
13. 创建第二个输出，并将其命名为 ChildRecords。 **SynchronousInputID**的新输出已设置为 None。 创建 3 个输出列：  
  
    -   ChildID（主键），类型为四字节有符号整数 [DT_I4]  
  
    -   ParentID（外键），类型也为四字节有符号整数 [DT_I4]  
  
    -   ChildRecord，类型为长度为 50 的字符串 [DT_STR]  
  
14. 上**脚本**页**脚本转换编辑器**，单击**编辑脚本**。 在**ScriptMain**类中，输入的代码示例所示。 关闭脚本开发环境和**脚本转换编辑器**。  
  
15. 向数据流添加 SQL Server 目标。 将脚本组件的 ParentRecords 输出连接到此目标。将此目标配置为使用 OLE DB 连接管理器和 Parents 表。  
  
16. 向数据流添加另一个 SQL Server 目标。 将脚本组件的 ChildRecords 输出连接到此目标。 将此目标配置为使用 OLE DB 连接管理器和 Children 表。  
  
17. 运行包。 包运行完毕后，检查两个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目标表中的父记录和子记录。  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
    Static nextRowIsParent As Boolean = False  
    Static parentCounter As Integer = 0  
    Static childCounter As Integer = 0  
  
    ' If current row starts with separator characters,  
    '  then following row contains new parent record.  
    If Row.Column0.StartsWith("***") Then  
        nextRowIsParent = True  
    Else  
        If nextRowIsParent Then  
            ' Current row contains parent record.  
            parentCounter += 1  
            Me.ParentRecordsBuffer.AddRow()  
            Me.ParentRecordsBuffer.ParentID = parentCounter  
            Me.ParentRecordsBuffer.ParentRecord = Row.Column0  
            nextRowIsParent = False  
        Else  
            ' Current row contains child record.  
            childCounter += 1  
            Me.ChildRecordsBuffer.AddRow()  
            Me.ChildRecordsBuffer.ChildID = childCounter  
            Me.ChildRecordsBuffer.ParentID = parentCounter  
            Me.ChildRecordsBuffer.ChildRecord = Row.Column0  
        End If  
    End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
    int static_Input0_ProcessInputRow_childCounter = 0;  
    int static_Input0_ProcessInputRow_parentCounter = 0;  
    bool static_Input0_ProcessInputRow_nextRowIsParent = false;  
  
        // If current row starts with separator characters,   
        // then following row contains new parent record.   
        if (Row.Column0.StartsWith("***"))  
        {  
            static_Input0_ProcessInputRow_nextRowIsParent = true;  
        }  
        else  
        {  
            if (static_Input0_ProcessInputRow_nextRowIsParent)  
            {  
                // Current row contains parent record.   
                static_Input0_ProcessInputRow_parentCounter += 1;  
                this.ParentRecordsBuffer.AddRow();  
                this.ParentRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ParentRecordsBuffer.ParentRecord = Row.Column0;  
                static_Input0_ProcessInputRow_nextRowIsParent = false;  
            }  
            else  
            {  
                // Current row contains child record.   
                static_Input0_ProcessInputRow_childCounter += 1;  
                this.ChildRecordsBuffer.AddRow();  
                this.ChildRecordsBuffer.ChildID = static_Input0_ProcessInputRow_childCounter;  
                this.ChildRecordsBuffer.ParentID = static_Input0_ProcessInputRow_parentCounter;  
                this.ChildRecordsBuffer.ChildRecord = Row.Column0;  
            }  
        }  
  
    }  
```  
  
## <a name="see-also"></a>另请参阅  
 [使用脚本组件创建同步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [使用脚本组件创建异步转换](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
  
  