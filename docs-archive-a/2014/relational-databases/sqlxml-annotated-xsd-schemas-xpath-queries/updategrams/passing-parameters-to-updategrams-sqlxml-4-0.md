---
title: Updategrams에 매개 변수 전달 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bc29de2dab3d0bc3587cb21b7005c0c23dcf7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652737"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a><span data-ttu-id="712fb-102">Updategram에 매개 변수 전달(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="712fb-102">Passing Parameters to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="712fb-103">Updategram은 템플릿이므로 Updategram에 매개 변수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-103">Updategrams are templates; therefore, you can pass them parameters.</span></span> <span data-ttu-id="712fb-104">템플릿에 매개 변수를 전달 하는 방법에 대 한 자세한 내용은 [Updategram 보안 고려 사항 &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="712fb-104">For more information about passing parameters to templates, see [Updategram Security Considerations &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="712fb-105">Updategram을 사용하면 NULL을 매개 변수 값으로 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-105">Updategrams allow you to pass NULL as a parameter value.</span></span> <span data-ttu-id="712fb-106">NULL 매개 변수 값을 전달하려면 `nullvalue` 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-106">To pass the NULL parameter value, you specify the `nullvalue` attribute.</span></span> <span data-ttu-id="712fb-107">그런 다음 `nullvalue` 특성에 할당된 값을 매개 변수 값으로 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-107">The value that is assigned to the `nullvalue` attribute is then provided as the parameter value.</span></span> <span data-ttu-id="712fb-108">Updategram은 이 값을 NULL로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-108">Updategrams treat this value as NULL.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="712fb-109">`<sql:header>` 및 `<updg:header>`에서는 `nullvalue`를 unqualified로 지정해야 하는 반면 `<updg:sync>`에서는 `nullvalue`를 qualified로 지정합니다(예: `updg:nullvalue`).</span><span class="sxs-lookup"><span data-stu-id="712fb-109">In `<sql:header>` and `<updg:header>`, you should specify the `nullvalue` as unqualified; whereas, in `<updg:sync>`, you specify the `nullvalue` as qualified (for example, `updg:nullvalue`).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="712fb-110">예</span><span class="sxs-lookup"><span data-stu-id="712fb-110">Examples</span></span>  
 <span data-ttu-id="712fb-111">다음 예제를 사용 하 여 작업 예제를 만들려면 [SQLXML 예를 실행 하기 위한 요구 사항](../../sqlxml/requirements-for-running-sqlxml-examples.md)에 지정 된 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-111">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="712fb-112">Updategram 예를 사용하기 전에 다음 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="712fb-112">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="712fb-113">이 예에서는 기본 매핑을 사용합니다. 즉, Updategram에 매핑 스키마가 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-113">The examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="712fb-114">매핑 스키마를 사용 하는 updategram의 추가 예제는 [Updategram &#40;SQLXML 4.0&#41;에서 주석이 추가 된 매핑 스키마 지정 ](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="712fb-114">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="a-passing-parameters-to-an-updategram"></a><span data-ttu-id="712fb-115">A.</span><span class="sxs-lookup"><span data-stu-id="712fb-115">A.</span></span> <span data-ttu-id="712fb-116">Updategram에 매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="712fb-116">Passing parameters to an updategram</span></span>  
 <span data-ttu-id="712fb-117">이 예에서 Updategram은 HumanResources.Shift 테이블에 있는 직원의 성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-117">In this example, the updategram changes the last name of an employee in the HumanResources.Shift table.</span></span> <span data-ttu-id="712fb-118">Updategram에는 두 개의 매개 변수인 ShiftID이 전달 됩니다 .이 매개 변수는 shift 및 Name을 고유 하 게 식별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-118">The updategram is passed two parameters: ShiftID, which is used to uniquely identify a shift, and Name.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="712fb-119">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="712fb-119">To test the updategram</span></span>  
  
1.  <span data-ttu-id="712fb-120">위의 Updategram을 메모장에 복사하고 UpdategramWithParameters.xml로 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-120">Copy the updategram above into Notepad and save it to file as UpdategramWithParameters.xml.</span></span>  
  
2.  <span data-ttu-id="712fb-121">다음 줄을 추가 하 여 sqlxml4test.vbs를 실행 하는 데 [ADO를 사용 하 여 sqlxml](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) 4.0 테스트 스크립트 ()를 준비 하 고 Sqlxml 4.0 쿼리를 실행 하 여 updategram를 실행 합니다 `cmd.Properties("Output Stream").Value = outStream` .</span><span class="sxs-lookup"><span data-stu-id="712fb-121">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a><span data-ttu-id="712fb-122">B.</span><span class="sxs-lookup"><span data-stu-id="712fb-122">B.</span></span> <span data-ttu-id="712fb-123">NULL을 매개 변수 값으로 Updategram에 전달</span><span class="sxs-lookup"><span data-stu-id="712fb-123">Passing NULL as a parameter value to an updategram</span></span>  
 <span data-ttu-id="712fb-124">Updategram을 실행하면 NULL로 설정할 매개 변수에 "isnull" 값이 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-124">In executing an updategram, the "isnull" value is assigned to the parameter that you want to set to NULL.</span></span> <span data-ttu-id="712fb-125">Updategram은 "isnulll" 매개 변수 값을 NULL로 변환하고 적절하게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-125">Updategram converts the "isnulll" parameter value to NULL and processes it accordingly.</span></span>  
  
 <span data-ttu-id="712fb-126">다음 Updategram에서는 직원 직함을 NULL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-126">The following updategram sets an employee title to NULL:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="712fb-127">Updategram을 테스트하려면</span><span class="sxs-lookup"><span data-stu-id="712fb-127">To test the updategram</span></span>  
  
1.  <span data-ttu-id="712fb-128">위의 Updategram을 메모장에 복사하고 UpdategramPassingNullvalues.xml로 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="712fb-128">Copy the updategram above into Notepad and save it to file as UpdategramPassingNullvalues.xml.</span></span>  
  
2.  <span data-ttu-id="712fb-129">다음 줄을 추가 하 여 sqlxml4test.vbs를 실행 하는 데 [ADO를 사용 하 여 sqlxml](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) 4.0 테스트 스크립트 ()를 준비 하 고 Sqlxml 4.0 쿼리를 실행 하 여 updategram를 실행 합니다 `cmd.Properties("Output Stream").Value = outStream` .</span><span class="sxs-lookup"><span data-stu-id="712fb-129">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="712fb-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="712fb-130">See Also</span></span>  
 [<span data-ttu-id="712fb-131">Updategram 보안 고려 사항은 SQLXML 4.0&#41;&#40;</span><span class="sxs-lookup"><span data-stu-id="712fb-131">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
