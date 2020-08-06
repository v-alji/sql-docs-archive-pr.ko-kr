---
title: '경고 속성: 새 경고 (옵션 페이지) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4a1507372aa1516c2a88b8682faa77a7d57e58f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737497"
---
# <a name="alert-properties-new-alert-options-page"></a><span data-ttu-id="678c2-102">경고 속성: 새 경고(옵션 페이지)</span><span class="sxs-lookup"><span data-stu-id="678c2-102">Alert Properties: New Alert (Options Page)</span></span>
  <span data-ttu-id="678c2-103">이 페이지를 사용 하 여 에이전트 경고에 대 한 옵션을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-103">Use this page to view and modify options for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts.</span></span>  
  
## <a name="options"></a><span data-ttu-id="678c2-104">옵션</span><span class="sxs-lookup"><span data-stu-id="678c2-104">Options</span></span>  
 <span data-ttu-id="678c2-105">**주소**</span><span class="sxs-lookup"><span data-stu-id="678c2-105">**E-mail**</span></span>  
 <span data-ttu-id="678c2-106">전자 메일 알림에 이벤트의 오류 텍스트(있는 경우)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-106">Include error text from the event, if any, in e-mail notifications.</span></span>  
  
 <span data-ttu-id="678c2-107">**호출기**</span><span class="sxs-lookup"><span data-stu-id="678c2-107">**Pager**</span></span>  
 <span data-ttu-id="678c2-108">호출기 알림에 이벤트의 오류 텍스트(있는 경우)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-108">Include error text from the event, if any, in pager notifications.</span></span>  
  
 <span data-ttu-id="678c2-109">**Net Send**</span><span class="sxs-lookup"><span data-stu-id="678c2-109">**Net send**</span></span>  
 <span data-ttu-id="678c2-110">Net Send 알림에 이벤트의 오류 텍스트(있는 경우)를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-110">Include error text from the event, if any, in net send notifications.</span></span>  
  
 <span data-ttu-id="678c2-111">**추가로 보낼 알림 메시지**</span><span class="sxs-lookup"><span data-stu-id="678c2-111">**Additional notification message to send**</span></span>  
 <span data-ttu-id="678c2-112">알림 메시지에 포함할 추가 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-112">Type any additional text to include in notification messages.</span></span>  
  
 <span data-ttu-id="678c2-113">**응답 간격**</span><span class="sxs-lookup"><span data-stu-id="678c2-113">**Delay between responses**</span></span>  
 <span data-ttu-id="678c2-114">이벤트의 반복된 발생에 대한 지연 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-114">Specify a delay for repeated occurrences of the event.</span></span> <span data-ttu-id="678c2-115">일부 이벤트는 짧은 기간 동안에 자주 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-115">Some events may occur frequently during a short period of time.</span></span> <span data-ttu-id="678c2-116">이 경우 이벤트가 발생했음을 알고 싶기는 하지만 모든 이벤트에 응답하고 싶지는 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-116">In this case, you may want to know that the event has occurred, but you may not want a response for every event.</span></span> <span data-ttu-id="678c2-117">제한 시간을 지정 하려면이 옵션을 사용 합니다. 지연이 발생 하는 경우 경고가 이벤트에 응답 하면 에이전트는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 지연 중 이벤트가 발생 하는지 여부에 관계 없이 다시 응답 하기 전에 지정 된 지연 시간 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-117">Use this option to specify a time-out. With a delay, after the alert responds to an event, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent waits for the delay specified before responding again, regardless of whether the event occurs during the delay.</span></span>  
  
 <span data-ttu-id="678c2-118">**내**</span><span class="sxs-lookup"><span data-stu-id="678c2-118">**Minutes**</span></span>  
 <span data-ttu-id="678c2-119">지연 시간을 분 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-119">Specify a delay in minutes.</span></span> <span data-ttu-id="678c2-120">이벤트가 발생할 때마다 응답하려면 0분 0초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-120">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
 <span data-ttu-id="678c2-121">**까지의**</span><span class="sxs-lookup"><span data-stu-id="678c2-121">**Seconds**</span></span>  
 <span data-ttu-id="678c2-122">지연 시간을 초 단위로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-122">Specify a delay in seconds.</span></span> <span data-ttu-id="678c2-123">이벤트가 발생할 때마다 응답하려면 0분 0초를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="678c2-123">To respond every time the event occurs, specify 0 minutes and 0 seconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678c2-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="678c2-124">See Also</span></span>  
 [<span data-ttu-id="678c2-125">경고</span><span class="sxs-lookup"><span data-stu-id="678c2-125">Alerts</span></span>](alerts.md)  
  
  
