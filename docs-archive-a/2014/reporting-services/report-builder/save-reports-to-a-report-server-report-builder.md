---
title: 보고서 서버에 보고서 저장(보고서 작성기) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 48dfef01-ed8c-4f23-90c3-de67c90a97dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80e35c447593e89d422e72ea31ec6be34c3619f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739430"
---
# <a name="save-reports-to-a-report-server-report-builder"></a><span data-ttu-id="0261f-102">보고서 서버에 보고서 저장(보고서 작성기)</span><span class="sxs-lookup"><span data-stu-id="0261f-102">Save Reports to a Report Server (Report Builder)</span></span>
  <span data-ttu-id="0261f-103">보고서 작성기에서는 보고서 정의를 보고서 서버에 저장할 수 있습니다(보고서 게시라고도 함).</span><span class="sxs-lookup"><span data-stu-id="0261f-103">In Report Builder, you can save a report definition to a report server (also known as publishing a report).</span></span> <span data-ttu-id="0261f-104">보고서를 보고서 서버에 저장하면 다른 사용자가 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-104">When the report is saved to a report server, other users can view the report.</span></span> <span data-ttu-id="0261f-105">게시된 보고서를 실행할 때마다 최신 데이터를 검색하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-105">Each time you run the published report, you will retrieve the most current data.</span></span> <span data-ttu-id="0261f-106">렌더링된 보고서의 정적 복사본을 저장하려면 보고서를 다른 파일 형식으로 내보내고 저장하거나, 보고서 기록 기능을 사용하여 렌더링된 보고서의 여러 버전을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-106">To save a static copy of a rendered report, export the report to a different file format and save it or use the report history feature to save versions of rendered reports.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0261f-107">보고서 정의를 저장한 위치와 관계없이 보고서를 미리 볼 때 보고서는 서버에서 처리되거나 로컬에서 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-107">The location of the saved report definition does not affect whether the report is processed on the server or processed locally when you preview the report.</span></span>  
  
### <a name="to-save-a-report-to-a-report-server"></a><span data-ttu-id="0261f-108">보고서 서버에 보고서를 저장하려면</span><span class="sxs-lookup"><span data-stu-id="0261f-108">To save a report to a report server</span></span>  
  
1.  <span data-ttu-id="0261f-109">보고서 작성기 단추에서 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="0261f-110">다른 **이름으로 저장** _\<Report Item\>_ 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-110">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0261f-111">보고서를 다시 저장하는 경우 보고서가 이전 위치에 자동으로 다시 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="0261f-112">다른 이름으로 저장 옵션을 사용하여 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-112">Use the Save As option to change location.</span></span>  
  
2.  <span data-ttu-id="0261f-113">필요한 경우 **최근에 사용한 사이트 및 서버** 를 클릭하여 최근에 사용한 보고서 서버와 SharePoint 사이트의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="0261f-114">보고서를 저장할 보고서 서버 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-114">Browse to the report server location where you want to save the report.</span></span>  
  
4.  <span data-ttu-id="0261f-115">**이름**에 보고서의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-115">In **Name**, type the name of the report.</span></span>  
  
5.  <span data-ttu-id="0261f-116">**항목 유형**에서 저장 중인 보고서 항목의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-116">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="0261f-117">보고서의 유형은 보고서 (\*.rdl)입니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-117">The type for reports is Reports(\*.rdl).</span></span>  
  
### <a name="to-save-a-report-as-a-different-name"></a><span data-ttu-id="0261f-118">보고서를 다른 이름으로 저장하려면</span><span class="sxs-lookup"><span data-stu-id="0261f-118">To save a report as a different name</span></span>  
  
1.  <span data-ttu-id="0261f-119">보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-119">From the Report Builder button, click **Save As**.</span></span> <span data-ttu-id="0261f-120">다른 **이름으로 저장** _\<Report Item\>_ 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-120">The **Save As**_\<Report Item\>_ dialog box opens.</span></span>  
  
2.  <span data-ttu-id="0261f-121">보고서를 저장할 보고서 서버 위치 또는 파일 공유로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-121">Browse to the report server location or to the file share where you want to save the report.</span></span>  
  
3.  <span data-ttu-id="0261f-122">**이름**에 보고서의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-122">In **Name**, type the name of the report.</span></span>  
  
4.  <span data-ttu-id="0261f-123">**항목 유형**에서 저장 중인 보고서 항목의 유형을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-123">In **Items of type**, select the type of report item you are saving.</span></span> <span data-ttu-id="0261f-124">보고서의 유형은 보고서 (\*.rdl)입니다.</span><span class="sxs-lookup"><span data-stu-id="0261f-124">The type for reports is Reports(\*.rdl).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0261f-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0261f-125">See Also</span></span>  
 <span data-ttu-id="0261f-126">[보고서 작성기 및 SSRS &#40;보고서 찾기, 보기 및 관리 &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0261f-126">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0261f-127">[보고서 &#40;보고서 작성기 및 SSRS&#41;내보내기](export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="0261f-127">[Exporting Reports &#40;Report Builder and SSRS&#41;](export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="0261f-128">[보고서 저장 &#40;보고서 작성기&#41;](saving-reports-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="0261f-128">[Saving Reports &#40;Report Builder&#41;](saving-reports-report-builder.md) </span></span>  
 [<span data-ttu-id="0261f-129">다른 파일 형식으로 보고서 내보내기&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0261f-129">Export a Report as Another File Type &#40;Report Builder and SSRS&#41;</span></span>](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)  
  
  
