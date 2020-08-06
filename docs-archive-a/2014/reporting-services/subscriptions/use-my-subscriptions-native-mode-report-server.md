---
title: 내 구독 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3378a65637ad04151cc517fd9047363af954c31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739094"
---
# <a name="use-my-subscriptions"></a><span data-ttu-id="8f62e-102">내 구독 사용</span><span class="sxs-lookup"><span data-stu-id="8f62e-102">Use My Subscriptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="8f62e-103">보고서 관리자에는 모든 구독을 한 곳으로 구성 하는 **내 구독** 페이지가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-103">Report Manager includes a **My Subscriptions** page that organizes all of your subscriptions into one place.</span></span> <span data-ttu-id="8f62e-104">내 구독을 사용하여 기존 구독을 보고, 수정하고, 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-104">You can use My Subscriptions to view, modify, and delete existing subscriptions.</span></span> <span data-ttu-id="8f62e-105">하지만 내 구독을 사용하여 구독을 만들 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-105">However, you cannot use it to create subscriptions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="8f62e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기본 모드</span><span class="sxs-lookup"><span data-stu-id="8f62e-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="8f62e-107">내 구독에서 폴더, 보고서, 설명, 트리거, 마지막 실행 또는 상태를 기준으로 구독을 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-107">Within My Subscriptions, you can sort subscriptions by folder, report, description, trigger, last run, or status.</span></span> <span data-ttu-id="8f62e-108">시간순으로 정렬되는 마지막 실행을 제외하고 모든 값은 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-108">All values are sorted alphabetically except for Last Run, which is in chronological order.</span></span>  
  
 <span data-ttu-id="8f62e-109">내 구독에는 사용자가 만든 구독만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-109">My Subscriptions shows only the subscriptions that you create.</span></span> <span data-ttu-id="8f62e-110">다른 사용자의 구독에 구독자로 추가되더라도 다른 사용자 소유의 구독은 나열되지 않으며 데이터 기반 구독도 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-110">It does not list subscriptions that are owned by other users, even if you are added as a subscriber to those subscriptions, nor does it show data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="8f62e-111">구독을 이름별로 검색할 수 없으며 트리거 정보, 상태 정보 등을 기준으로 구독을 검색할 수도 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-111">You cannot search for subscriptions by name, nor can you search for subscriptions based on trigger information, status information, and so forth.</span></span> <span data-ttu-id="8f62e-112">자세한 내용은 [기본 모드&#41;에서 표준 구독 만들기, 수정 및 삭제 &#40;Reporting Services ](create-and-manage-subscriptions-for-native-mode-report-servers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8f62e-112">For more information, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
## <a name="how-to-use-my-subscriptions"></a><span data-ttu-id="8f62e-113">내 구독 사용 방법</span><span class="sxs-lookup"><span data-stu-id="8f62e-113">How to Use My Subscriptions</span></span>  
 <span data-ttu-id="8f62e-114">내 구독은 보고서 관리자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-114">My Subscriptions is available through Report Manager.</span></span> <span data-ttu-id="8f62e-115">내 구독에 액세스하려면 보고서 관리자 일반 도구 모음에서 **내 구독** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-115">To access My Subscriptions, click **My Subscriptions** on the Report Manager global toolbar.</span></span>  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a><span data-ttu-id="8f62e-116">Windows PowerShell을 사용하여 MySubscriptions 나열</span><span class="sxs-lookup"><span data-stu-id="8f62e-116">Use Windows PowerShell to list MySubscriptions</span></span>  
 <span data-ttu-id="8f62e-117">![PowerShell 관련 콘텐츠](../media/rs-powershellicon.jpg "PowerShell 관련 콘텐츠")</span><span class="sxs-lookup"><span data-stu-id="8f62e-117">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
 <span data-ttu-id="8f62e-118">다음 PowerShell 스크립트는 현재 사용자의 구독 목록 및 구독 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8f62e-118">The following PowerShell script will return the list of subscriptions and subscription properties for the current user.</span></span> <span data-ttu-id="8f62e-119">자세한 내용은 [ReportingService2010.ListMySubscriptions 메서드](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8f62e-119">For more information, see [ReportingService2010.ListMySubscriptions Method](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).</span></span>  
  
```powershell
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions
```  
  
## <a name="see-also"></a><span data-ttu-id="8f62e-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f62e-120">See Also</span></span>  
 <span data-ttu-id="8f62e-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="8f62e-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="8f62e-122">[구독 및 배달&#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8f62e-122">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="8f62e-123">기본 모드 보고서 서버 구독 만들기 및 관리</span><span class="sxs-lookup"><span data-stu-id="8f62e-123">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../create-manage-subscriptions-native-mode-report-servers.md)  
