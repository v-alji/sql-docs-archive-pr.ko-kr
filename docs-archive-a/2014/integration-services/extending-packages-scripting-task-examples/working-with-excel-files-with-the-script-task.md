---
title: 스크립트 태스크를 사용한 Excel 파일 작업 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68a764452de548cd46e74d2a7f2f588a050a21c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651203"
---
# <a name="working-with-excel-files-with-the-script-task"></a><span data-ttu-id="6e4dc-102">스크립트 태스크를 사용한 Excel 파일 작업</span><span class="sxs-lookup"><span data-stu-id="6e4dc-102">Working with Excel Files with the Script Task</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<span data-ttu-id="6e4dc-103">에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 파일 형식으로 스프레드시트에 저장된 데이터를 작업하기 위한 Excel 연결 관리자, Excel 원본 및 Excel 대상을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-103">provides the Excel connection manager, Excel source, and Excel destination for working with data stored in spreadsheets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel file format.</span></span> <span data-ttu-id="6e4dc-104">이 항목에서는 스크립트 태스크를 사용하여 사용 가능한 Excel 데이터베이스(통합 문서 파일) 및 테이블(워크시트 및 명명된 범위)에 대한 정보를 가져오는 기술을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-104">The techniques described in this topic use the Script task to obtain information about available Excel databases (workbook files) and tables (worksheets and named ranges).</span></span> <span data-ttu-id="6e4dc-105">이러한 예제는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB 공급자가 지원하는 다른 파일 기반 데이터 원본에도 사용할 수 있도록 쉽게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-105">These samples can easily be modified to work with any of the other file-based data sources supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider.</span></span>  
  
 [<span data-ttu-id="6e4dc-106">예제를 테스트하기 위한 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="6e4dc-106">Configuring a Package to Test the Samples</span></span>](#configuring)  
  
 [<span data-ttu-id="6e4dc-107">예 1: Excel 파일의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e4dc-107">Example1: Check Whether an Excel File Exists</span></span>](#example1)  
  
 [<span data-ttu-id="6e4dc-108">예 2: Excel 테이블의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e4dc-108">Example 2: Check Whether an Excel Table Exists</span></span>](#example2)  
  
 [<span data-ttu-id="6e4dc-109">예 3: 폴더의 Excel 파일 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6e4dc-109">Example 3: Get a List of Excel Files in a Folder</span></span>](#example3)  
  
 [<span data-ttu-id="6e4dc-110">예 4: Excel 파일의 테이블 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6e4dc-110">Example 4: Get a List of Tables in an Excel File</span></span>](#example4)  
  
 [<span data-ttu-id="6e4dc-111">샘플 결과 표시</span><span class="sxs-lookup"><span data-stu-id="6e4dc-111">Displaying the Results of the Samples</span></span>](#testing)  
  
> [!NOTE]  
>  <span data-ttu-id="6e4dc-112">여러 패키지에서 쉽게 다시 사용할 수 있는 태스크를 만들려면 이 스크립트 태스크 예제에 있는 코드를 바탕으로 사용자 지정 태스크를 만들어 보십시오.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-112">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="6e4dc-113">자세한 내용은 [사용자 지정 태스크 개발](../extending-packages-custom-objects/task/developing-a-custom-task.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-113">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="configuring-a-package-to-test-the-samples"></a><a name="configuring"></a><span data-ttu-id="6e4dc-114">예제를 테스트 하기 위한 패키지 구성</span><span class="sxs-lookup"><span data-stu-id="6e4dc-114">Configuring a Package to Test the Samples</span></span>  
 <span data-ttu-id="6e4dc-115">단일 패키지에서 이 항목의 모든 예제를 테스트할 수 있도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-115">You can configure a single package to test all the samples in this topic.</span></span> <span data-ttu-id="6e4dc-116">이 항목의 예제에서는 대개 동일한 여러 패키지 변수와 동일한 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-116">The samples use many of the same package variables and the same [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes.</span></span>  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a><span data-ttu-id="6e4dc-117">패키지를 이 항목의 예에 사용할 수 있도록 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-117">To configure a package for use with the examples in this topic</span></span>  
  
1.  <span data-ttu-id="6e4dc-118">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 새 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 프로젝트를 만들고 편집을 위해 기본 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-118">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open the default package for editing.</span></span>  
  
2.  <span data-ttu-id="6e4dc-119">**변수**.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-119">**Variables**.</span></span> <span data-ttu-id="6e4dc-120">**변수** 창을 열고 다음 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-120">Open the **Variables** window and define the following variables:</span></span>  
  
    -   <span data-ttu-id="6e4dc-121">`String` 형식의 `ExcelFile`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-121">`ExcelFile`, of type `String`.</span></span> <span data-ttu-id="6e4dc-122">기존 Excel 통합 문서의 전체 경로와 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-122">Enter the complete path and filename to an existing Excel workbook.</span></span>  
  
    -   <span data-ttu-id="6e4dc-123">`String` 형식의 `ExcelTable`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-123">`ExcelTable`, of type `String`.</span></span> <span data-ttu-id="6e4dc-124">기존 워크시트의 이름이나 `ExcelFile` 변수의 값에 명명된 통합 문서의 명명된 범위를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-124">Enter the name of an existing worksheet or named range in the workbook named in the value of the `ExcelFile` variable.</span></span> <span data-ttu-id="6e4dc-125">이 값은 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-125">This value is case-sensitive.</span></span>  
  
    -   <span data-ttu-id="6e4dc-126">`Boolean` 형식의 `ExcelFileExists`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-126">`ExcelFileExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="6e4dc-127">`Boolean` 형식의 `ExcelTableExists`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-127">`ExcelTableExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="6e4dc-128">`String` 형식의 `ExcelFolder`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-128">`ExcelFolder`, of type `String`.</span></span> <span data-ttu-id="6e4dc-129">적어도 하나의 Excel 통합 문서가 들어 있는 폴더의 전체 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-129">Enter the complete path of a folder that contains at least one Excel workbook.</span></span>  
  
    -   <span data-ttu-id="6e4dc-130">`Object` 형식의 `ExcelFiles`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-130">`ExcelFiles`, of type `Object`.</span></span>  
  
    -   <span data-ttu-id="6e4dc-131">`Object` 형식의 `ExcelTables`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-131">`ExcelTables`, of type `Object`.</span></span>  
  
3.  <span data-ttu-id="6e4dc-132">**Imports 문**.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-132">**Imports statements**.</span></span> <span data-ttu-id="6e4dc-133">대부분의 코드 예제에서는 스크립트 파일의 맨 위에서 다음 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 네임스페이스 중 하나 또는 둘 모두를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-133">Most of the code samples require you to import one or both of the following [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces at the top of your script file:</span></span>  
  
    -   <span data-ttu-id="6e4dc-134">`System.IO` - 파일 시스템 작업의 경우</span><span class="sxs-lookup"><span data-stu-id="6e4dc-134">`System.IO`, for file system operations.</span></span>  
  
    -   <span data-ttu-id="6e4dc-135">`System.Data.OleDb` - Excel 파일을 데이터 원본으로 열려는 경우</span><span class="sxs-lookup"><span data-stu-id="6e4dc-135">`System.Data.OleDb`, to open Excel files as data sources.</span></span>  
  
4.  <span data-ttu-id="6e4dc-136">**참조**.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-136">**References**.</span></span> <span data-ttu-id="6e4dc-137">Excel 파일에서 스키마 정보를 읽는 코드 예제에는 스크립트 프로젝트에는 `System.Xml` 네임스페이스에 대한 추가 참조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-137">The code samples that read schema information from Excel files require an additional reference in the script project to the `System.Xml` namespace.</span></span>  
  
5.  <span data-ttu-id="6e4dc-138">**옵션** 대화 상자의 **일반** 페이지에 있는 **스크립트 언어** 옵션을 사용하여 스크립트 구성 요소에 대한 기본 스크립트 언어를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-138">Set the default scripting language for the Script component by using the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="6e4dc-139">자세한 내용은 [General Page](../general-page-of-integration-services-designers-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-139">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
##  <a name="example-1-description-check-whether-an-excel-file-exists"></a><a name="example1"></a> <span data-ttu-id="6e4dc-140">예 1 설명: Excel 파일의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e4dc-140">Example 1 Description: Check Whether an Excel File Exists</span></span>  
 <span data-ttu-id="6e4dc-141">이 예에서는 `ExcelFile` 변수에 지정된 Excel 통합 문서 파일이 존재하는지 확인한 다음 `ExcelFileExists` 변수의 부울 값을 이 결과로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-141">This example determines whether the Excel workbook file specified in the `ExcelFile` variable exists, and then sets the Boolean value of the `ExcelFileExists` variable to the result.</span></span> <span data-ttu-id="6e4dc-142">이 부울 값은 패키지의 워크플로에서 분기하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-142">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6e4dc-143">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-143">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6e4dc-144">패키지에 새 스크립트 태스크를 추가 하 고 이름을로 변경 `ExcelFileExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-144">Add a new Script task to the package and change its name to `ExcelFileExists`.</span></span>  
  
2.  <span data-ttu-id="6e4dc-145">**스크립트 태스크 편집기**의 **스크립트** 탭에서 **ReadOnlyVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-145">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-146">`ExcelFile`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-146">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="6e4dc-147">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-147">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-148">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 변수를 선택 `ExcelFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-148">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFile` variable.</span></span>  
  
3.  <span data-ttu-id="6e4dc-149">**ReadWriteVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-149">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-150">`ExcelFileExists`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-150">Type `ExcelFileExists`.</span></span>  
  
         <span data-ttu-id="6e4dc-151">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-151">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-152">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 변수를 선택 `ExcelFileExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-152">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFileExists` variable.</span></span>  
  
4.  <span data-ttu-id="6e4dc-153">**스크립트 편집**을 클릭하여 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-153">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="6e4dc-154">`Imports` 네임스페이스에 대한 `System.IO` 문을 스크립트 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-154">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="6e4dc-155">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-155">Add the following code.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="6e4dc-156">예 1 코드</span><span class="sxs-lookup"><span data-stu-id="6e4dc-156">Example 1 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example-2-description-check-whether-an-excel-table-exists"></a><a name="example2"></a> <span data-ttu-id="6e4dc-157">예 2 설명: Excel 테이블의 존재 여부 확인</span><span class="sxs-lookup"><span data-stu-id="6e4dc-157">Example 2 Description: Check Whether an Excel Table Exists</span></span>  
 <span data-ttu-id="6e4dc-158">이 예에서는 `ExcelTable` 변수에 지정된 Excel 워크시트 또는 명명된 범위가 `ExcelFile` 변수에 지정된 Excel 통합 문서 파일에 있는지 여부를 확인한 다음 `ExcelTableExists` 변수의 부울 값을 이 결과로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-158">This example determines whether the Excel worksheet or named range specified in the `ExcelTable` variable exists in the Excel workbook file specified in the `ExcelFile` variable, and then sets the Boolean value of the `ExcelTableExists` variable to the result.</span></span> <span data-ttu-id="6e4dc-159">이 부울 값은 패키지의 워크플로에서 분기하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-159">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6e4dc-160">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-160">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6e4dc-161">패키지에 새 스크립트 태스크를 추가 하 고 이름을로 변경 `ExcelTableExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-161">Add a new Script task to the package and change its name to `ExcelTableExists`.</span></span>  
  
2.  <span data-ttu-id="6e4dc-162">**스크립트 태스크 편집기**의 **스크립트** 탭에서 **ReadOnlyVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-162">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-163">`ExcelTable` `ExcelFile` 쉼표로 구분 하 여 입력`.`</span><span class="sxs-lookup"><span data-stu-id="6e4dc-163">Type `ExcelTable` and `ExcelFile` separated by commas`.`</span></span>  
  
         <span data-ttu-id="6e4dc-164">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-164">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-165">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 `ExcelTable` 및 변수를 선택 `ExcelFile` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-165">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTable` and `ExcelFile` variables.</span></span>  
  
3.  <span data-ttu-id="6e4dc-166">**ReadWriteVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-166">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-167">`ExcelTableExists`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-167">Type `ExcelTableExists`.</span></span>  
  
         <span data-ttu-id="6e4dc-168">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-168">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-169">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 변수를 선택 `ExcelTableExists` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-169">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTableExists` variable.</span></span>  
  
4.  <span data-ttu-id="6e4dc-170">**스크립트 편집**을 클릭하여 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-170">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="6e4dc-171">스크립트 프로젝트에 `System.Xml` 어셈블리에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-171">Add a reference to the `System.Xml` assembly in the script project.</span></span>  
  
6.  <span data-ttu-id="6e4dc-172">`Imports` 및 `System.IO` 네임스페이스에 대한 `System.Data.OleDb` 문을 스크립트 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-172">Add `Imports` statements for the `System.IO` and `System.Data.OleDb` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="6e4dc-173">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-173">Add the following code.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="6e4dc-174">예 2 코드</span><span class="sxs-lookup"><span data-stu-id="6e4dc-174">Example 2 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example-3-description-get-a-list-of-excel-files-in-a-folder"></a><a name="example3"></a> <span data-ttu-id="6e4dc-175">예 3 설명: 폴더의 Excel 파일 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6e4dc-175">Example 3 Description: Get a List of Excel Files in a Folder</span></span>  
 <span data-ttu-id="6e4dc-176">이 예에서는 `ExcelFolder` 변수 값에 지정된 폴더에 있는 Excel 파일의 목록으로 배열을 채운 다음 이 배열을 `ExcelFiles` 변수에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-176">This example fills an array with the list of Excel files found in the folder specified in the value of the `ExcelFolder` variable, and then copies the array into the `ExcelFiles` variable.</span></span> <span data-ttu-id="6e4dc-177">Foreach from Variable 열거자를 사용하여 배열의 파일을 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-177">You can use the Foreach from Variable enumerator to iterate over the files in the array.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6e4dc-178">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-178">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6e4dc-179">패키지에 새 스크립트 태스크를 추가하고 해당 이름을 **GetExcelFiles**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-179">Add a new Script task to the package and change its name to **GetExcelFiles**.</span></span>  
  
2.  <span data-ttu-id="6e4dc-180">**스크립트 태스크 편집기**를 열고 **스크립트** 탭에서 **ReadOnlyVariables**를 클릭한 후 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-180">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-181">`ExcelFolder` 입력</span><span class="sxs-lookup"><span data-stu-id="6e4dc-181">Type `ExcelFolder`</span></span>  
  
         <span data-ttu-id="6e4dc-182">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-182">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-183">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 excel 폴더 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-183">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFolder variable.</span></span>  
  
3.  <span data-ttu-id="6e4dc-184">**ReadWriteVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-184">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-185">`ExcelFiles`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-185">Type `ExcelFiles`.</span></span>  
  
         <span data-ttu-id="6e4dc-186">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-186">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-187">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 ExcelFiles 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-187">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFiles variable.</span></span>  
  
4.  <span data-ttu-id="6e4dc-188">**스크립트 편집**을 클릭하여 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-188">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="6e4dc-189">`Imports` 네임스페이스에 대한 `System.IO` 문을 스크립트 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-189">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="6e4dc-190">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-190">Add the following code.</span></span>  
  
### <a name="example-3-code"></a><span data-ttu-id="6e4dc-191">예 3 코드</span><span class="sxs-lookup"><span data-stu-id="6e4dc-191">Example 3 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="6e4dc-192">대체 솔루션</span><span class="sxs-lookup"><span data-stu-id="6e4dc-192">Alternate Solution</span></span>  
 <span data-ttu-id="6e4dc-193">스크립트 태스크를 사용하여 Excel 파일의 목록을 배열로 수집하는 대신 ForEach File 열거자를 사용하여 폴더의 모든 Excel 파일을 반복할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-193">Instead of using a Script task to gather a list of Excel files into an array, you can also use the ForEach File enumerator to iterate over all the Excel files in a folder.</span></span> <span data-ttu-id="6e4dc-194">자세한 내용은 [Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑](../control-flow/foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-194">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="example-4-description-get-a-list-of-tables-in-an-excel-file"></a><a name="example4"></a> <span data-ttu-id="6e4dc-195">예 4 설명: Excel 파일의 테이블 목록 가져오기</span><span class="sxs-lookup"><span data-stu-id="6e4dc-195">Example 4 Description: Get a List of Tables in an Excel File</span></span>  
 <span data-ttu-id="6e4dc-196">이 예에서는 `ExcelFile` 변수 값으로 지정된 Excel 통합 문서 파일에 있는 워크시트 및 명명된 범위의 목록으로 배열을 채운 다음 이 배열을 `ExcelTables`에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-196">This example fills an array with the list of worksheets and named ranges found in the Excel workbook file specified by the value of the `ExcelFile` variable, and then copies the array into the `ExcelTables` variable.</span></span> <span data-ttu-id="6e4dc-197">Foreach from Variable 열거자를 사용하여 배열의 테이블을 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-197">You can use the Foreach from Variable Enumerator to iterate over the tables in the array.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6e4dc-198">Excel 통합 문서의 테이블 목록에는 워크시트($ 접미사를 가짐)와 명명된 범위가 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-198">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="6e4dc-199">워크시트만 포함하거나 명명된 범위 목록만 포함하도록 목록을 필터링해야 하는 경우에는 이를 위한 다른 코드를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-199">If you have to filter the list for only worksheets or only named ranges, you may have to add additional code for this purpose.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="6e4dc-200">이 스크립트 태스크 예를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-200">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="6e4dc-201">패키지에 새 스크립트 태스크를 추가하고 해당 이름을 **GetExcelTables**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-201">Add a new Script task to the package and change its name to **GetExcelTables**.</span></span>  
  
2.  <span data-ttu-id="6e4dc-202">**스크립트 태스크 편집기**를 열고 **스크립트** 탭에서 **ReadOnlyVariables**를 클릭한 후 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-202">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-203">`ExcelFile`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-203">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="6e4dc-204">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-204">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-205">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 excel 파일 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-205">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFile variable.</span></span>  
  
3.  <span data-ttu-id="6e4dc-206">**ReadWriteVariables**를 클릭하고 다음 방법 중 하나를 사용하여 속성 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-206">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="6e4dc-207">`ExcelTables`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-207">Type `ExcelTables`.</span></span>  
  
         <span data-ttu-id="6e4dc-208">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-208">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-209">속성 필드 옆에 있는 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 excel 필드 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-209">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelTablesvariable.</span></span>  
  
4.  <span data-ttu-id="6e4dc-210">**스크립트 편집**을 클릭하여 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-210">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="6e4dc-211">스크립트 프로젝트에 `System.Xml` 네임스페이스에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-211">Add a reference to the `System.Xml` namespace in the script project.</span></span>  
  
6.  <span data-ttu-id="6e4dc-212">`Imports` 네임스페이스에 대한 `System.Data.OleDb` 문을 스크립트 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-212">Add an `Imports` statement for the `System.Data.OleDb` namespace at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="6e4dc-213">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-213">Add the following code.</span></span>  
  
### <a name="example-4-code"></a><span data-ttu-id="6e4dc-214">예 4 코드</span><span class="sxs-lookup"><span data-stu-id="6e4dc-214">Example 4 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="6e4dc-215">대체 솔루션</span><span class="sxs-lookup"><span data-stu-id="6e4dc-215">Alternate Solution</span></span>  
 <span data-ttu-id="6e4dc-216">스크립트 태스크를 사용하여 Excel 테이블의 목록을 배열로 수집하는 대신 ForEach ADO.NET 스키마 행 집합 열거자를 사용하여 Excel 통합 문서 파일의 모든 테이블, 즉 워크시트와 명명된 범위를 반복할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-216">Instead of using a Script task to gather a list of Excel tables into an array, you can also use the ForEach ADO.NET Schema Rowset Enumerator to iterate over all the tables (that is, worksheets and named ranges) in an Excel workbook file.</span></span> <span data-ttu-id="6e4dc-217">자세한 내용은 [Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑](../control-flow/foreach-loop-container.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-217">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="displaying-the-results-of-the-samples"></a><a name="testing"></a> <span data-ttu-id="6e4dc-218">예제 결과 표시</span><span class="sxs-lookup"><span data-stu-id="6e4dc-218">Displaying the Results of the Samples</span></span>  
 <span data-ttu-id="6e4dc-219">이 항목의 각 예를 동일한 패키지에서 구성한 경우 모든 스크립트 태스크를 모든 예의 출력을 표시하는 추가 스크립트 태스크에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-219">If you have configured each of the examples in this topic in the same package, you can connect all the Script tasks to an additional Script task that displays the output of all the examples.</span></span>  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a><span data-ttu-id="6e4dc-220">이 항목의 예 출력을 표시하도록 스크립트 태스크를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="6e4dc-220">To configure a Script task to display the output of the examples in this topic</span></span>  
  
1.  <span data-ttu-id="6e4dc-221">패키지에 새 스크립트 태스크를 추가하고 해당 이름을 **DisplayResults**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-221">Add a new Script task to the package and change its name to **DisplayResults**.</span></span>  
  
2.  <span data-ttu-id="6e4dc-222">각 태스크가 이전 태스크가 성공적으로 완료된 후 실행되도록 네 개의 예 스크립트 태스크를 서로 연결하고, 네 번째 예 태스크를 **DisplayResults** 태스크에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-222">Connect each of the four example Script tasks to one another, so that each task runs after the preceding task completes successfully, and connect the fourth example task to the **DisplayResults** task.</span></span>  
  
3.  <span data-ttu-id="6e4dc-223">**스크립트 태스크 편집기**에서 **DisplayResults** 태스크를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-223">Open the **DisplayResults** task in the **Script Task Editor**.</span></span>  
  
4.  <span data-ttu-id="6e4dc-224">**스크립트** 탭에서 **ReadOnlyVariables**를 클릭하고 다음 방법 중 하나를 사용하여 [예제를 테스트하기 위한 패키지 구성](#configuring)에 나열된 7개의 변수를 모두 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-224">On the **Script** tab, click **ReadOnlyVariables** and use one of the following methods to add all seven variables listed in [Configuring a Package to Test the Samples](#configuring):</span></span>  
  
    -   <span data-ttu-id="6e4dc-225">각 변수의 이름을 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-225">Type the name of each variable separated by commas.</span></span>  
  
         <span data-ttu-id="6e4dc-226">또는</span><span class="sxs-lookup"><span data-stu-id="6e4dc-226">-or-</span></span>  
  
    -   <span data-ttu-id="6e4dc-227">속성 필드 옆의 줄임표 (**...**) 단추를 클릭 하 고 **변수 선택** 대화 상자에서 변수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-227">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, selecting the variables.</span></span>  
  
5.  <span data-ttu-id="6e4dc-228">**스크립트 편집**을 클릭하여 스크립트 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-228">Click **Edit Script** to open the script editor.</span></span>  
  
6.  <span data-ttu-id="6e4dc-229">`Imports` 및 `Microsoft.VisualBasic` 네임스페이스에 대한 `System.Windows.Forms` 문을 스크립트 파일의 맨 위에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-229">Add `Imports` statements for the `Microsoft.VisualBasic` and `System.Windows.Forms` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="6e4dc-230">다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-230">Add the following code.</span></span>  
  
8.  <span data-ttu-id="6e4dc-231">패키지를 실행하고 메시지 상자에 표시된 결과를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-231">Run the package and examine the results displayed in a message box.</span></span>  
  
### <a name="code-to-display-the-results"></a><span data-ttu-id="6e4dc-232">결과를 표시하는 코드</span><span class="sxs-lookup"><span data-stu-id="6e4dc-232">Code to Display the Results</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
<span data-ttu-id="6e4dc-233">![Integration Services 아이콘 (작은 아이콘)](../media/dts-16.gif "Integration Services 아이콘(작은 아이콘)")  **은 최신 상태로 유지 Integration Services**</span><span class="sxs-lookup"><span data-stu-id="6e4dc-233">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="6e4dc-234">Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-234">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="6e4dc-235">MSDN의 Integration Services 페이지를 방문하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-235">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="6e4dc-236">이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.</span><span class="sxs-lookup"><span data-stu-id="6e4dc-236">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4dc-237">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e4dc-237">See Also</span></span>  
 <span data-ttu-id="6e4dc-238">[Excel 연결 관리자](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="6e4dc-238">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="6e4dc-239">Foreach 루프 컨테이너를 사용하여 Excel 파일 및 테이블 루핑</span><span class="sxs-lookup"><span data-stu-id="6e4dc-239">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
  
