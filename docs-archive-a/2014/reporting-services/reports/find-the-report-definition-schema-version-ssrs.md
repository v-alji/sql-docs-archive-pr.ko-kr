---
title: 보고서 정의 스키마 버전 찾기(SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- XML schemas [Reporting Services]
- Report Definition Language, XML schema
- schemas [Reporting Services]
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 413a270a3722ddda1f418c748fa5b7fba50dfeea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732396"
---
# <a name="find-the-report-definition-schema-version-ssrs"></a><span data-ttu-id="12f63-102">보고서 정의 스키마 버전 찾기(SSRS)</span><span class="sxs-lookup"><span data-stu-id="12f63-102">Find the Report Definition Schema Version (SSRS)</span></span>
  <span data-ttu-id="12f63-103">보고서 정의 파일은 rdl 파일의 유효성을 검사하는 데 사용되는 보고서 정의 스키마의 버전에 대한 RDL 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-103">A report definition file specifies the RDL namespace for the version of the report definition schema that is used to validate the rdl file.</span></span> <span data-ttu-id="12f63-104">보고서가 이전 네임스페이스용으로 작성된 경우 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 보고서 디자이너 또는 보고서 작성기와 같은 보고서 제작 환경에서 .rdl 파일을 열면 백업 파일이 자동으로 만들어지고 보고서가 현재 네임스페이스로 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-104">When you open an .rdl file in a report authoring environment such as Report Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or Report Builder, if the report was created for a previous namespace, a backup file is automatically created, and the report is upgraded to the current namespace.</span></span> <span data-ttu-id="12f63-105">업그레이드된 보고서 정의를 저장하면 변환된 .rdl 파일이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-105">If you save the upgraded report definition, you have saved the converted .rdl file.</span></span> <span data-ttu-id="12f63-106">이 방법은 보고서 정의를 업그레이드할 수 있는 유일한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-106">This is the only way to upgrade a report definition.</span></span> <span data-ttu-id="12f63-107">보고서 정의 자체는 보고서 서버에서 업그레이드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-107">The report definition itself is not upgraded on a report server.</span></span> <span data-ttu-id="12f63-108">컴파일된 보고서는 보고서 서버에서 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-108">The compiled report is upgraded on a report server.</span></span> <span data-ttu-id="12f63-109">자세한 내용은 [Upgrade Reports](../install-windows/upgrade-reports.md)을(를) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12f63-109">For more information, see [Upgrade Reports](../install-windows/upgrade-reports.md).</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-a-report"></a><span data-ttu-id="12f63-110">방법: 보고서의 RDL 스키마 버전 확인</span><span class="sxs-lookup"><span data-stu-id="12f63-110">How to: Identify the RDL Schema Version of a Report</span></span>  
  
1.  <span data-ttu-id="12f63-111">xml을 볼 수 있는 메모장이나 XML 메모장 2007과 같은 애플리케이션에서 보고서 .rdl 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-111">Open the report .rdl file in an application such as Notepad or XML Notepad 2007 in which you can view the xml.</span></span>  
  
     <span data-ttu-id="12f63-112">XML 보고서 요소는 스키마 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-112">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="12f63-113">예를 들어 다음 보고서 요소는 보고서 디자이너에 대한 네임스페이스와 보고서 정의에 대한 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-113">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="12f63-114">보고서 정의 네임스페이스는 다음 URL `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`(으)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-114">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`.</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-of-report-designer"></a><span data-ttu-id="12f63-115">방법: 보고서 디자이너의 RDL 스키마 버전 확인</span><span class="sxs-lookup"><span data-stu-id="12f63-115">How to: Identify the RDL Schema Version of Report Designer</span></span>  
  
1.  <span data-ttu-id="12f63-116">새 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-116">Open a new project.</span></span> <span data-ttu-id="12f63-117">선택한 프로젝트의 버전에 따라 RDL 스키마 버전이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-117">The version of the project that you choose determines the version of the RDL schema.</span></span> <span data-ttu-id="12f63-118">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서는 둘 이상의 스키마 버전이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-118">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], more than one schema version is supported.</span></span> <span data-ttu-id="12f63-119">자세한 내용은 [SQL Server Data Tools의 배포 및 버전 지원&#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-119">For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="12f63-120">**프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-120">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="12f63-121">**새 항목 추가** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-121">The **Add New Item** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="12f63-122">**템플릿** 창에서 **보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-122">In the **Templates** pane, click **Report**.</span></span>  
  
4.  <span data-ttu-id="12f63-123">**이름**에 보고서 이름을 입력하거나 기본 이름을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-123">In **Name**, type a report name or accept the default.</span></span>  
  
5.  <span data-ttu-id="12f63-124">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-124">Click **Add**.</span></span> <span data-ttu-id="12f63-125">보고서 디자이너의 디자인 뷰에 새 보고서가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-125">Report Designer opens a new blank report in Design view.</span></span>  
  
6.  <span data-ttu-id="12f63-126">**보기** 메뉴에서 **코드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-126">On the **View** menu, click **Code**.</span></span> <span data-ttu-id="12f63-127">보고서 정의가 XML 파일로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-127">The report definition is displayed as an XML file.</span></span>  
  
     <span data-ttu-id="12f63-128">XML 보고서 요소는 스키마 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-128">The XML Report element specifies the schema namespace.</span></span> <span data-ttu-id="12f63-129">예를 들어 다음 보고서 요소는 보고서 디자이너에 대한 네임스페이스와 보고서 정의에 대한 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-129">For example, the following Report element specifies the namespace for Report Designer and the namespace for the report definition.</span></span>  
  
    ```  
    <Report xmlns:rd=https://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     <span data-ttu-id="12f63-130">보고서 정의 네임스페이스는 다음 URL `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="12f63-130">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
### <a name="how-to-identify-the-rdl-schema-version-on-the-report-server"></a><span data-ttu-id="12f63-131">방법: 보고서 서버의 RDL 스키마 버전 확인</span><span class="sxs-lookup"><span data-stu-id="12f63-131">How to: Identify the RDL Schema Version on the Report Server</span></span>  
  
-   <span data-ttu-id="12f63-132">보고서 관리자에서 보고서 서버의 URL을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-132">In Report Manager, type the URL for the report server.</span></span> <span data-ttu-id="12f63-133">예를 들어 다음 URL은 로컬 컴퓨터의 보고서 서버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-133">For example, the following URL specifies a report server on the local computer:</span></span>  
  
     `http://localhost/reportserver/reportdefinition.xsd`  
  
     <span data-ttu-id="12f63-134">.xsd 파일이 브라우저에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-134">The .xsd file opens in the browser.</span></span>  
  
     <span data-ttu-id="12f63-135">XML 스키마 요소는 스키마 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-135">The XML schema element specifies the schema namespace.</span></span> <span data-ttu-id="12f63-136">예를 들어 다음 스키마 요소는 3개의 네임스페이스, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 내부적으로 사용되는 targetNamespace 참조, 스키마 자체에 대한 xsd 참조(xsd) 및 보고서 정의 참조를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="12f63-136">For example, the following schema element specifies three namespaces: the targetNamespace reference that is used internally by [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], the xsd reference for the schema itself (xsd), and the report definition reference.</span></span>  
  
    ```  
    <xsd:schema   
    targetNamespace="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     <span data-ttu-id="12f63-137">보고서 정의 네임스페이스는 다음 URL `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span><span class="sxs-lookup"><span data-stu-id="12f63-137">The report definition namespace is specified by the following URL: `https://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f63-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="12f63-138">See Also</span></span>  
 <span data-ttu-id="12f63-139">[보고서 업그레이드](../install-windows/upgrade-reports.md) </span><span class="sxs-lookup"><span data-stu-id="12f63-139">[Upgrade Reports](../install-windows/upgrade-reports.md) </span></span>  
 [<span data-ttu-id="12f63-140">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="12f63-140">Report Definition Language &#40;SSRS&#41;</span></span>](report-definition-language-ssrs.md)  
  
  
