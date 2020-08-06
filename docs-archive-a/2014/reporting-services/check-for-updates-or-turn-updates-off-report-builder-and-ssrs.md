---
title: 업데이트 확인 또는 업데이트 해제 (보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9c69792d-d7c4-453b-ae2f-6d2d071d8606
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 088d41e71d770f746367f2760cff8ff67b15623c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650793"
---
# <a name="check-for-updates-or-turn-updates-off-report-builder-and-ssrs"></a><span data-ttu-id="8f6ce-102">업데이트 확인 또는 업데이트 해제(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="8f6ce-102">Check for Updates or Turn Updates Off (Report Builder and SSRS)</span></span>
  <span data-ttu-id="8f6ce-103">보고서를 열 때마다 보고서 작성기는 해당 보고서에 있는 보고서 파트의 게시된 인스턴스가 보고서 서버 또는 보고서 서버와 통합된 SharePoint 사이트에서 업데이트되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-103">Every time you open a report, Report Builder checks to see if the published instances of report parts in that report have been updated on the report server or SharePoint site integrated with a report server.</span></span> <span data-ttu-id="8f6ce-104">또한 데이터 세트 및 매개 변수와 같은 보고서 파트의 종속 항목에서 변경 내용을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-104">It also checks for changes in the report parts' dependent items, such as the dataset and parameters.</span></span> <span data-ttu-id="8f6ce-105">보고서 파트나 보고서 파트의 종속성이 사이트 또는 서버에서 업데이트되었으면 보고서의 알림 표시줄에 업데이트된 파트의 수가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-105">If any report parts or their dependencies have been updated on the site or server, an information bar in your report displays the number of updated parts.</span></span> <span data-ttu-id="8f6ce-106">업데이트를 확인하고 허용 또는 거부하도록 선택하거나 알림 표시줄을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-106">You can choose to view and accept or reject the updates, or dismiss the information bar.</span></span>  
  
 <span data-ttu-id="8f6ce-107">알림 표시줄을 사용하지 않도록 설정하고 보고서 파트의 게시된 인스턴스가 변경된 경우 알림을 받지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-107">You can also disable the information bar and not be informed if published instances of report parts have changed.</span></span> <span data-ttu-id="8f6ce-108">이것은 사용자 설정이므로 사용자가 여는 모든 보고서에 대해 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-108">This is a user setting; it will be disabled for all reports that you open.</span></span> <span data-ttu-id="8f6ce-109">알림 표시줄을 사용하지 않도록 설정한 경우에도 여전히 업데이트를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-109">Even if you have disabled the information bar, you can still check for updates.</span></span>  
  
### <a name="to-turn-on-and-off-report-part-updates"></a><span data-ttu-id="8f6ce-110">보고서 파트 업데이트를 설정 및 해제하려면</span><span class="sxs-lookup"><span data-stu-id="8f6ce-110">To turn on and off report part updates</span></span>  
  
1.  <span data-ttu-id="8f6ce-111">보고서 작성기 단추를 클릭 한 다음 **옵션**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-111">Click the Report Builder button, and then click **Options**.</span></span>  
  
2.  <span data-ttu-id="8f6ce-112">**옵션** 대화 상자의 **리소스** 탭에서 **내 보고서의 보고서 파트에 대 한 업데이트 표시** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-112">In the **Options** dialog box, on the **Resources** tab, select or clear the **Show updates to report parts in my reports** check box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8f6ce-113">이것은 사용자 설정이므로</span><span class="sxs-lookup"><span data-stu-id="8f6ce-113">This is a user setting.</span></span> <span data-ttu-id="8f6ce-114">사용자가 여는 모든 보고서에 대해 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-114">It will be disabled for all reports that you open.</span></span>  
  
### <a name="to-check-for-updates"></a><span data-ttu-id="8f6ce-115">업데이트를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="8f6ce-115">To check for updates</span></span>  
  
-   <span data-ttu-id="8f6ce-116">보고서 외부의 디자인 화면 또는 보고서 본문을 마우스 오른쪽 단추로 클릭 하 고 **업데이트 확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f6ce-116">Right-click the design surface outside the report, or in the report body, and click **Check for Updates**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6ce-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f6ce-117">See Also</span></span>  
 <span data-ttu-id="8f6ce-118">[보고서 파트 &#40;보고서 작성기 및 SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8f6ce-118">[Report Parts &#40;Report Builder and SSRS&#41;](report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8f6ce-119">[보고서 파트 게시 및 다시 게시 &#40;보고서 작성기 및 SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8f6ce-119">[Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;](report-design/publish-and-republish-report-parts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8f6ce-120">[보고서 파트를 검색 하 고 기본 폴더 &#40;보고서 작성기 및 SSRS를 설정&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8f6ce-120">[Browse for Report Parts and Set a Default Folder &#40;Report Builder and SSRS&#41;](report-design/browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="8f6ce-121">[보고서 파트 &#40;보고서 작성기 및 SSRS에 대 한 문제 해결&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="8f6ce-121">[Troubleshoot Report Parts &#40;Report Builder and SSRS&#41;](../../2014/reporting-services/troubleshoot-report-parts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="8f6ce-122">보고서 작성기의 보고서 파트 및 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="8f6ce-122">Report Parts and Datasets in Report Builder</span></span>](report-data/report-parts-and-datasets-in-report-builder.md)  
  
  
