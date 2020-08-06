---
title: Microsoft Access에서 보고서 가져오기 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653749"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a><span data-ttu-id="4d3e3-102">Microsoft Access에서 보고서 가져오기(Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="4d3e3-102">Import Reports from Microsoft Access (Reporting Services)</span></span>
  <span data-ttu-id="4d3e3-103">보고서 디자이너 Access 데이터베이스 또는 프로젝트에서 보고서를 가져올 수 있습니다 [!INCLUDE[msCoName](../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d3e3-103">In Report Designer, you can import reports from a [!INCLUDE[msCoName](../includes/msconame-md.md)] Access database or project.</span></span> <span data-ttu-id="4d3e3-104">단, 보고서 디자이너가 설치되어 있는 컴퓨터에 Access 2002 이상이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-104">Access 2002 or a later version must be installed on the same computer on which Report Designer is installed.</span></span>  
  
 <span data-ttu-id="4d3e3-105">가져오기 기능을 사용하면 데이터베이스나 프로젝트 파일의 모든 보고서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-105">When you use the import feature, all reports in the database or project file are imported.</span></span> <span data-ttu-id="4d3e3-106">Access 파일에 보고서가 많이 있을 경우 보고서를 가져올 개별 보고서 프로젝트를 만든 후 주 보고서 프로젝트에서 각 RDL 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-106">If your Access file contains many reports, you may want to create a separate report project into which to import the reports, and then open the individual RDL files in your main report project.</span></span> <span data-ttu-id="4d3e3-107">보고서를 보고서 디자이너로 가져와야 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-107">You can edit the reports after they are imported into Report Designer.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="4d3e3-108">에서 일부 Access 보고서 개체는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-108">does not support all Access report objects.</span></span> <span data-ttu-id="4d3e3-109">변환 되지 않은 항목은 **작업 목록** 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-109">Items that are not converted are displayed in the **Task List** window.</span></span> <span data-ttu-id="4d3e3-110">자세한 내용은 [SSRS&#41;&#40;지원 되는 액세스 보고서 기능 ](../../2014/reporting-services/supported-access-report-features-ssrs.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-110">For more information, see [Supported Access Report Features &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).</span></span>  
  
### <a name="to-import-reports-from-microsoft-access"></a><span data-ttu-id="4d3e3-111">Microsoft Access에서 보고서를 가져오려면</span><span class="sxs-lookup"><span data-stu-id="4d3e3-111">To import reports from Microsoft Access</span></span>  
  
1.  <span data-ttu-id="4d3e3-112">보고서를 가져올 프로젝트를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-112">Open or create a project into which to import the reports.</span></span>  
  
2.  <span data-ttu-id="4d3e3-113">**프로젝트** 메뉴에서 **보고서 가져오기**를 가리킨 다음 **Microsoft Access**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-113">On the **Project** menu, point to **Import Reports**, and then click **Microsoft Access**.</span></span> <span data-ttu-id="4d3e3-114">또는 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **보고서 가져오기**를 가리킨 다음 **Microsoft Access**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-114">Alternatively, right-click the project in Solution Explorer, point to **Import Reports**, and then click **Microsoft Access**.</span></span>  
  
3.  <span data-ttu-id="4d3e3-115">**열기** 대화 상자에서 보고서가 포함 된 Access 데이터베이스 (.mdb, .accdb) 또는 프로젝트 (.adp)를 선택한 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-115">In the **Open** dialog box, select the Access database (.mdb, .accdb) or project (.adp) that contains the reports, and then click **Open**.</span></span> <span data-ttu-id="4d3e3-116">그러면 데이터베이스 또는 프로젝트 파일의 모든 보고서가 가져와지고 솔루션 탐색기의 보고서 폴더에 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-116">All the reports in the database or project file are imported and listed in the Reports folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="4d3e3-117">빌드 오류에 대 한 **작업 목록** 창을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-117">Check the **Task List** window for build errors.</span></span> <span data-ttu-id="4d3e3-118">**작업 목록** 창을 보려면 **보기** 메뉴를 열고 **다른 창**을 가리킨 다음 **작업 목록**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d3e3-118">To view the **Task List** window, open the **View** menu, point to **Other Windows**, and then click **Task List**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3e3-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d3e3-119">See Also</span></span>  
 [<span data-ttu-id="4d3e3-120">보고서 디자이너로 보고서 디자인&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="4d3e3-120">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
