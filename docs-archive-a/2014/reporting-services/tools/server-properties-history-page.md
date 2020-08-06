---
title: 서버 속성(기록 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df5ff9dc7a94431f8feec112d460938aa1631ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652007"
---
# <a name="server-properties-history-page"></a><span data-ttu-id="ee36c-102">서버 속성(기록 페이지)</span><span class="sxs-lookup"><span data-stu-id="ee36c-102">Server Properties (History Page)</span></span>
  <span data-ttu-id="ee36c-103">이 페이지를 사용하여 보관할 보고서 기록 복사본 수의 기본값을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-103">Use this page to set a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="ee36c-104">이 기본값은 모든 보고서에 대한 보고서 기록 제한을 설정하는 초기 설정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-104">The default value provides an initial setting that establishes report history limits for all reports.</span></span> <span data-ttu-id="ee36c-105">이 설정은 보고서마다 다르게 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-105">You can vary these settings for individual reports.</span></span>  
  
 <span data-ttu-id="ee36c-106">보고서 기록은 스냅샷이 만들어진 시점의 보고서에 대한 현재 보고서 데이터 및 레이아웃을 포함하는 보고서 스냅샷 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-106">Report history is a collection of report snapshots that include report data and layout that is current for the report at the time the snapshot is created.</span></span> <span data-ttu-id="ee36c-107">보고서 기록을 사용하여 특정 날짜 또는 시간의 보고서 복사본을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-107">You can use report history to keep a copy of a report as it was on a specific date or time.</span></span> <span data-ttu-id="ee36c-108">기본 모드 보고서 서버, 또는 SharePoint 통합 모드로 구성된 보고서 서버에서 실행되는 개별 보고서에 대해 보고서 기록을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-108">You can create and manage report history for individual reports that run on a native mode report server or a report server that is configured for SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="ee36c-109">보고서 기록 스냅샷은 보고서 서버 데이터베이스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-109">Report history snapshots are stored in the report server database.</span></span> <span data-ttu-id="ee36c-110">스냅샷을 무제한으로 보관하는 경우 데이터베이스 크기를 정기적으로 점검하여 너무 빠른 속도로 커지거나 지나치게 많은 디스크 공간을 소모하지 않도록 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ee36c-110">If you keep an unlimited number of snapshots, be sure to periodically check the database size to ensure it is not growing too fast or consuming too much disk space.</span></span>  
  
 <span data-ttu-id="ee36c-111">이 페이지를 열려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 시작하고 보고서 서버 인스턴스에 연결한 다음 보고서 서버 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-111">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="ee36c-112">**기록** 을 클릭하여 이 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-112">Click **History** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ee36c-113">옵션</span><span class="sxs-lookup"><span data-stu-id="ee36c-113">Options</span></span>  
 <span data-ttu-id="ee36c-114">**보고서 기록에 스냅샷을 무제한으로 보관**</span><span class="sxs-lookup"><span data-stu-id="ee36c-114">**Keep an unlimited number of snapshots in report history**</span></span>  
 <span data-ttu-id="ee36c-115">모든 보고서 기록 스냅샷을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-115">Retain all report history snapshots.</span></span> <span data-ttu-id="ee36c-116">보고서 기록 크기를 줄이려면 스냅샷을 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-116">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
 <span data-ttu-id="ee36c-117">**보고서 기록의 복사본 개수 제한**</span><span class="sxs-lookup"><span data-stu-id="ee36c-117">**Limit the copies of report history**</span></span>  
 <span data-ttu-id="ee36c-118">설정된 수의 보고서 기록 스냅샷을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-118">Retain a set number of report history snapshots.</span></span> <span data-ttu-id="ee36c-119">한도에 이르면 새 복사본의 저장 공간을 만들기 위해 보고서 기록에서 오래된 복사본이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-119">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="ee36c-120">나중에 보고서 기록을 제한하면 기존 보고서 기록이 지정한 제한을 초과하는 경우 보고서 서버에서 기존 보고서 기록을 새 제한으로 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-120">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="ee36c-121">가장 오래된 보고서 스냅샷이 먼저 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-121">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="ee36c-122">보고서 기록이 비어 있거나 제한보다 적은 경우 새 보고서 스냅샷이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-122">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="ee36c-123">한도에 이르면 새 보고서 스냅샷이 추가될 때 가장 오래된 스냅샷이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="ee36c-123">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee36c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ee36c-124">See Also</span></span>  
 <span data-ttu-id="ee36c-125">[보고서 서버 속성 &#40;Management Studio&#41;설정](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee36c-125">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="ee36c-126">[Management Studio에서 보고서 서버에 연결](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="ee36c-126">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="ee36c-127">Management Studio의 보고서 서버 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="ee36c-127">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
