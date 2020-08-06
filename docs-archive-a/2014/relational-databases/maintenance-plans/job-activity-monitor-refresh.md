---
title: 작업 활동 모니터 새로 고침 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f290825f8a776c954ef802b184f7600aea5dc9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650973"
---
# <a name="job-activity-monitor-refresh"></a><span data-ttu-id="608b8-102">작업 활동 모니터 새로 고침</span><span class="sxs-lookup"><span data-stu-id="608b8-102">Job Activity Monitor Refresh</span></span>
  <span data-ttu-id="608b8-103">**새로 고침 설정** 대화 상자를 사용하여 작업 활동 모니터가 서버 작업에 대한 새로운 정보를 가져오는 간격을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-103">Use the **Refresh Settings** dialog box to configure how often Job Activity Monitor obtains new information about server activity.</span></span> <span data-ttu-id="608b8-104">작업 활동 모니터 표에 정보를 가져오려면 작업 활동 모니터가 모니터링하는 서버에 대해 쿼리를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-104">Job Activity Monitor must run queries on the monitored server to obtain information for the Job Activity Monitor grid.</span></span> <span data-ttu-id="608b8-105">자동 새로 고침 간격을 30초보다 작게 설정하면 이러한 쿼리를 실행하는 데 사용되는 시간이 서버 성능에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-105">When the auto-refresh interval is set to less than 30 seconds, the time used to run these queries can affect server performance.</span></span>  
  
 <span data-ttu-id="608b8-106">이 대화 상자를 열려면 작업 활동 모니터에서 **상태**섹션의 **새로 고침 설정 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-106">To open this dialog, click **View refresh settings**, in the **Status** section of Job Activity Monitor.</span></span>  
  
## <a name="options"></a><span data-ttu-id="608b8-107">옵션</span><span class="sxs-lookup"><span data-stu-id="608b8-107">Options</span></span>  
 <span data-ttu-id="608b8-108">**자동 새로 고침 간격**</span><span class="sxs-lookup"><span data-stu-id="608b8-108">**Auto-refresh every**</span></span>  
 <span data-ttu-id="608b8-109">작업 모니터 정보의 자동 새로 고침을 시작하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-109">Check to initiate automatic refreshing of Activity Monitor information.</span></span> <span data-ttu-id="608b8-110">이 옵션은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-110">This is off by default.</span></span>  
  
 <span data-ttu-id="608b8-111">**초**</span><span class="sxs-lookup"><span data-stu-id="608b8-111">**seconds**</span></span>  
 <span data-ttu-id="608b8-112">자동 새로 고침 시도 간격(초)입니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-112">The number of seconds between auto-refresh attempts.</span></span> <span data-ttu-id="608b8-113">기본값은 60초입니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-113">Defaults to 60 seconds.</span></span> <span data-ttu-id="608b8-114">5 이하로 설정하면 5초마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="608b8-114">Refreshes every 5 seconds when set to 5 or less.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608b8-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="608b8-115">See Also</span></span>  
 [<span data-ttu-id="608b8-116">작업 활동 모니터링</span><span class="sxs-lookup"><span data-stu-id="608b8-116">Monitor Job Activity</span></span>](../../ssms/agent/monitor-job-activity.md)  
  
  
