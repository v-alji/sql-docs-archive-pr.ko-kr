---
title: '2 단원: xsd 도구를 사용 하 여 RDL 스키마에서 클래스 생성 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2c5db118ad8f94afc72cea44b9a2489f2b4fd7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734703"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a><span data-ttu-id="9ad0f-102">2단원: xsd 도구를 사용하여 RDL 스키마에서 클래스 생성</span><span class="sxs-lookup"><span data-stu-id="9ad0f-102">Lesson 2: Generate Classes from the RDL Schema using the xsd Tool</span></span>
  <span data-ttu-id="9ad0f-103">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 만든 후 다음 단계는 보고서 정의 스키마의 로컬 복사본을 검색하고 XML 스키마 정의 도구(Xsd.exe)를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-103">After you have created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project, the next step is to retrieve a local copy of the report definition schema and run the XML Schema Definition Tool (Xsd.exe).</span></span>  
  
### <a name="to-generate-the-rdl-classes"></a><span data-ttu-id="9ad0f-104">RDL 클래스를 생성하려면</span><span class="sxs-lookup"><span data-stu-id="9ad0f-104">To generate the RDL classes</span></span>  
  
1.  <span data-ttu-id="9ad0f-105">[!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 또는 이에 상당하는 웹 브라우저 인스턴스를 열고 다음 URL로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-105">Open an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer (or equivalent Web browser) and navigate to the following URL:</span></span>  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  <span data-ttu-id="9ad0f-106">RDL 스키마가 브라우저에서 열렸으면 **파일** 메뉴에서 **다른 이름으로 저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-106">Once the RDL schema has been opened in the browser, browse to the **File** menu, and select **Save As**.</span></span>  
  
3.  <span data-ttu-id="9ad0f-107">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트를 만든 위치를 찾아 스키마를 ReportDefinition.xsd라는 이름으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-107">Browse to the location where you created your [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] project and save the schema with the file name ReportDefinition.xsd.</span></span>  
  
4.  <span data-ttu-id="9ad0f-108">파일이 저장되었으면 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 명령 프롬프트의 인스턴스를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-108">After the file has been saved, open an instance of the [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] command prompt.</span></span> <span data-ttu-id="9ad0f-109">명령 프롬프트의 인스턴스를 열려면 시작 메뉴를 클릭하고 **모든 프로그램**, **Microsoft Visual Studio 2010**, **Visual Studio Tools** 를 차례로 가리킨 다음 **Visual Studio 명령 프롬프트(2010)** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-109">To open an instance of the command prompt, click the Start menu, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools** and click **Visual Studio Command Prompt (2010)**.</span></span>  
  
5.  <span data-ttu-id="9ad0f-110">현재 경로를 ReportDefinition.xsd 파일을 저장한 위치로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-110">Change the current path to the location where you saved the ReportDefinition.xsd file:</span></span>  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  <span data-ttu-id="9ad0f-111">다음 명령을 사용하여 RDL 스키마에 대한 클래스가 있는 ReportDefinition.cs 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-111">Generate the ReportDefinition.cs file that contains the classes for the RDL schema with the following command:</span></span>  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     <span data-ttu-id="9ad0f-112">ReportDefinition.vb 파일을 생성하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-112">To generate a ReportDefinition.vb file use this command:</span></span>  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  <span data-ttu-id="9ad0f-113">프로젝트에 ReportDefinition.xsd를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-113">Add ReportDefinition.xsd your project.</span></span> <span data-ttu-id="9ad0f-114">**프로젝트** 메뉴에서 **기존 항목 추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-114">From the **Project** menu, click **Add Existing Item**.</span></span> <span data-ttu-id="9ad0f-115">ReportDefinition.xsd 파일의 위치로 이동하여 ReportDefinition.xsd를 선택한 다음 **추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-115">Browse to the location of the ReportDefinition.xsd file, select ReportDefinition.xsd, and click **Add**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9ad0f-116">프로젝트에 ReportDefinition.xsd 파일을 추가한 후에도 **솔루션 탐색기** 에 ReportDefinition.cs(.vb) 파일이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-116">After you have added the ReportDefinition.xsd file to the project you will notice in **Solution Explorer** that the ReportDefinition.cs (.vb) file is not there.</span></span> <span data-ttu-id="9ad0f-117">파일을 표시하려면 ReportDefinition.xsd 파일 옆에 있는 확장/축소 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-117">To display the file, click the expand/collapse button next to the ReportDefinition.xsd file.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="9ad0f-118">다음 단원</span><span class="sxs-lookup"><span data-stu-id="9ad0f-118">Next Lesson</span></span>  
 <span data-ttu-id="9ad0f-119">다음 단원에서는 RDL 스키마에서 생성한 클래스를 사용하여 보고서 서버에서 보고서 정의를 로드하는 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-119">In the next lesson, you will write code to load a report definition from a report server using the classes you generated from the RDL schema.</span></span> <span data-ttu-id="9ad0f-120">[Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ad0f-120">See [Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad0f-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ad0f-121">See Also</span></span>  
 <span data-ttu-id="9ad0f-122">[RDL 스키마 &#40;생성 된 클래스를 사용 하 여 보고서 업데이트 (SSRS 자습서&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="9ad0f-122">[Updating Reports Using Classes Generated from the RDL Schema &#40;SSRS Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md) </span></span>  
 [<span data-ttu-id="9ad0f-123">보고서 정의 언어&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9ad0f-123">Report Definition Language &#40;SSRS&#41;</span></span>](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
