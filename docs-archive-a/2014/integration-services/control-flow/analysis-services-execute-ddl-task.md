---
title: Analysis Services DDL 실행 태스크 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.f1
helpviewer_keywords:
- Analysis Services Execute DDL task
- DDL
ms.assetid: 7f25c8c6-b601-41f2-9553-be0a2ee0751a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a75bae174c816cdabd07ce688e068cbadb016b45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651209"
---
# <a name="analysis-services-execute-ddl-task"></a><span data-ttu-id="764ef-102">Analysis Services DDL 실행 태스크</span><span class="sxs-lookup"><span data-stu-id="764ef-102">Analysis Services Execute DDL Task</span></span>
  <span data-ttu-id="764ef-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크는 큐브 및 차원과 같은 다차원 개체와 마이닝 모델을 만들거나 삭제 또는 변경할 수 있는 DDL(데이터 정의 언어) 문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task runs data definition language (DDL) statements that can create, drop, or alter mining models and multidimensional objects such as cubes and dimensions.</span></span> <span data-ttu-id="764ef-104">예를 들어 DDL 문은 **Adventure Works** 큐브에 파티션을 만들거나 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]에 포함된 예제 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 차원을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-104">For example, a DDL statement can create a partition in the **Adventure Works** cube, or delete a dimension in [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="764ef-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 연결 관리자를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-105">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="764ef-106">자세한 내용은 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="764ef-106">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="764ef-107">에는 분석 개체 처리, 데이터 마이닝 예측 쿼리 실행 등의 비즈니스 인텔리전스 작업을 수행하는 많은 태스크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-107">includes a number of tasks that perform business intelligence operations, such as processing analytic objects and running data mining prediction queries.</span></span>  
  
 <span data-ttu-id="764ef-108">관련 비즈니스 인텔리전스 태스크에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="764ef-108">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="764ef-109">Analysis Services 처리 태스크</span><span class="sxs-lookup"><span data-stu-id="764ef-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
-   [<span data-ttu-id="764ef-110">데이터 마이닝 쿼리 태스크</span><span class="sxs-lookup"><span data-stu-id="764ef-110">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="ddl-statements"></a><span data-ttu-id="764ef-111">DDL 문</span><span class="sxs-lookup"><span data-stu-id="764ef-111">DDL Statements</span></span>  
 <span data-ttu-id="764ef-112">DDL 문은 ASSL( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) 문으로 표현되고 XML for Analysis(XMLA) 명령에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-112">The DDL statements are represented as statements in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language (ASSL), and framed in an XML for Analysis (XMLA) command.</span></span>  
  
-   <span data-ttu-id="764ef-113">ASSL은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스와 이 인스턴스에 포함된 데이터베이스 및 데이터베이스 개체를 정의하고 설명하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-113">ASSL is used to define and describe an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and the databases and database objects it contains.</span></span> <span data-ttu-id="764ef-114">자세한 내용은 [Analysis Services 스크립팅 언어 &#40;,&#41; 참조](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="764ef-114">For more information, see [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).</span></span>  
  
-   <span data-ttu-id="764ef-115">XMLA는 만들기, 변경 또는 처리와 같은 동작 명령을 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스로 보내는 데 사용하는 명령 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-115">XMLA is a command language that is used to send action commands, such as Create, Alter, or Process, to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="764ef-116">자세한 내용은 [XMLA&#40;XML for Analysis&#41; 참조](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="764ef-116">For more information, see [XML for Analysis  &#40;XMLA&#41; Reference](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).</span></span>  
  
 <span data-ttu-id="764ef-117">DDL 코드가 별도의 파일에 저장되어 있을 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크는 파일 연결 관리자를 사용하여 해당 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-117">If the DDL code is stored in a separate file, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL task uses a File connection manager to specify the path of the file.</span></span> <span data-ttu-id="764ef-118">자세한 내용은 [File Connection Manager](../connection-manager/file-connection-manager.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="764ef-118">For more information, see [File Connection Manager](../connection-manager/file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="764ef-119">DDL 문은 암호와 기타 중요한 정보를 포함할 수 있으므로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] DDL 실행 태스크가 하나 이상 포함된 패키지는 패키지 보호 수준 `EncryptAllWithUserKey` 또는 `EncryptAllWithPassword`를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-119">Because DDL statements can contain passwords and other sensitive information, a package that contains one or more [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Execute DDL tasks should use the package protection level `EncryptAllWithUserKey` or `EncryptAllWithPassword`.</span></span> <span data-ttu-id="764ef-120">자세한 내용은 [Integration Services&#40;SSIS&#41; 패키지](../integration-services-ssis-packages.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="764ef-120">For more information, see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md).</span></span>  
  
### <a name="ddl-examples"></a><span data-ttu-id="764ef-121">DDL 예</span><span class="sxs-lookup"><span data-stu-id="764ef-121">DDL Examples</span></span>  
 <span data-ttu-id="764ef-122">다음 3개의 DDL 문은 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]에 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 스크립팅 개체에 의해 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-122">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="764ef-123">다음 DDL 문은 **Promotion** 차원을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-123">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="764ef-124">다음 DDL 문은 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 큐브를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-124">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="764ef-125">다음 DDL 문은 **Forecasting** 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-125">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
 <span data-ttu-id="764ef-126">다음 3개의 DDL 문은 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)]에 포함된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 스크립팅 개체에 의해 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-126">The following three DDL statements were generated by scripting objects in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)], the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database included in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="764ef-127">다음 DDL 문은 **Promotion** 차원을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-127">The following DDL statement deletes the **Promotion** dimension.</span></span>  
  
```  
<Delete xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <DimensionID>Dim Promotion</DimensionID>  
    </Object>  
</Delete>  
  
```  
  
 <span data-ttu-id="764ef-128">다음 DDL 문은 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 큐브를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-128">The following DDL statement processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] cube.</span></span>  
  
```  
<Batch xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Parallel>  
    <Process xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
      <Object>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      </Object>  
      <Type>ProcessFull</Type>  
      <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
    </Process>  
  </Parallel>  
</Batch>  
  
```  
  
 <span data-ttu-id="764ef-129">다음 DDL 문은 **Forecasting** 마이닝 모델을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-129">The following DDL statement creates the **Forecasting** mining model.</span></span>  
  
```  
<Create xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <ParentObject>  
        <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
        <MiningStructureID>Forecasting</MiningStructureID>  
    </ParentObject>  
    <ObjectDefinition>  
        <MiningModel xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
            <ID>Forecasting</ID>  
            <Name>Forecasting</Name>  
            <Algorithm>Microsoft_Time_Series</Algorithm>  
            <AlgorithmParameters>  
                <AlgorithmParameter>  
                    <Name>PERIODICITY_HINT</Name>  
                    <Value xsi:type="xsd:string">{12}</Value>  
                </AlgorithmParameter>  
            </AlgorithmParameters>  
            <Columns>  
                <Column>  
                    <ID>Amount</ID>  
                    <Name>Amount</Name>  
                    <SourceColumnID>Amount</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Model Region</ID>  
                    <Name>Model Region</Name>  
                    <SourceColumnID>Model Region</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
                <Column>  
                    <ID>Quantity</ID>  
                    <Name>Quantity</Name>  
                    <SourceColumnID>Quantity</SourceColumnID>  
                    <Usage>Predict</Usage>  
                </Column>  
                <Column>  
                    <ID>Time Index</ID>  
                    <Name>Time Index</Name>  
                    <SourceColumnID>Time Index</SourceColumnID>  
                    <Usage>Key</Usage>  
                </Column>  
            </Columns>  
            <Collation>Latin1_General_CS_AS_KS</Collation>  
        </MiningModel>  
    </ObjectDefinition>  
</Create>  
  
```  
  
## <a name="configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="764ef-130">Analysis Services DDL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="764ef-130">Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="764ef-131">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="764ef-131">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="764ef-132">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="764ef-132">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="764ef-133">Analysis Services DDL 실행 태스크 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="764ef-133">Analysis Services Execute DDL Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="764ef-134">Analysis Services DDL 실행 태스크 편집기&#40;DDL 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="764ef-134">Analysis Services Execute DDL Task Editor &#40;DDL Page&#41;</span></span>](../analysis-services-execute-ddl-task-editor-ddl-page.md)  
  
-   [<span data-ttu-id="764ef-135">식 페이지</span><span class="sxs-lookup"><span data-stu-id="764ef-135">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="764ef-136">[!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 이러한 속성을 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="764ef-136">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="764ef-137">태스크 또는 컨테이너의 속성 설정</span><span class="sxs-lookup"><span data-stu-id="764ef-137">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-execute-ddl-task"></a><span data-ttu-id="764ef-138">프로그래밍 방식으로 Analysis Services DDL 실행 태스크 구성</span><span class="sxs-lookup"><span data-stu-id="764ef-138">Programmatic Configuration of the Analysis Services Execute DDL Task</span></span>  
 <span data-ttu-id="764ef-139">이러한 속성을 프로그래밍 방식으로 설정하는 방법을 보려면 다음 항목을 클릭하십시오.</span><span class="sxs-lookup"><span data-stu-id="764ef-139">For more information about programmatically setting these properties, click the following topic:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.ASExecuteDDLTask>  
  
  
