---
title: PreConnect:Starting 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
author: stevestein
ms.author: sstein
ms.openlocfilehash: 67b642d369c73cc144af31f835786613766045f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652806"
---
# <a name="preconnectstarting-event-class"></a><span data-ttu-id="118c2-102">PreConnect:Starting 이벤트 클래스</span><span class="sxs-lookup"><span data-stu-id="118c2-102">PreConnect:Starting Event Class</span></span>
  <span data-ttu-id="118c2-103">PreConnect:Starting 이벤트 클래스는 LOGON 트리거나 리소스 관리자 분류자 함수가 언제 실행을 시작하는지 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="118c2-103">The PreConnect:Starting event class indicates when a LOGON trigger or the Resource Governor classifier function starts execution.</span></span>  
  
## <a name="preconnectstarting-event-class-data-columns"></a><span data-ttu-id="118c2-104">PreConnect:Starting 이벤트 클래스 데이터 열</span><span class="sxs-lookup"><span data-stu-id="118c2-104">PreConnect:Starting Event Class Data Columns</span></span>  
  
|<span data-ttu-id="118c2-105">데이터 열 이름</span><span class="sxs-lookup"><span data-stu-id="118c2-105">Data column name</span></span>|<span data-ttu-id="118c2-106">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="118c2-106">Data type</span></span>|<span data-ttu-id="118c2-107">Description</span><span class="sxs-lookup"><span data-stu-id="118c2-107">Description</span></span>|<span data-ttu-id="118c2-108">열 ID</span><span class="sxs-lookup"><span data-stu-id="118c2-108">Column ID</span></span>|<span data-ttu-id="118c2-109">필터 가능</span><span class="sxs-lookup"><span data-stu-id="118c2-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="118c2-110">EventClass</span><span class="sxs-lookup"><span data-stu-id="118c2-110">EventClass</span></span>|`int`|<span data-ttu-id="118c2-111">215</span><span class="sxs-lookup"><span data-stu-id="118c2-111">215</span></span>|<span data-ttu-id="118c2-112">27</span><span class="sxs-lookup"><span data-stu-id="118c2-112">27</span></span>|<span data-ttu-id="118c2-113">예</span><span class="sxs-lookup"><span data-stu-id="118c2-113">No</span></span>|  
|<span data-ttu-id="118c2-114">SPID</span><span class="sxs-lookup"><span data-stu-id="118c2-114">SPID</span></span>|`int`|<span data-ttu-id="118c2-115">이 이벤트를 발생시키는 서버 프로세스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="118c2-115">The ID of server process that fires this event.</span></span>|<span data-ttu-id="118c2-116">12</span><span class="sxs-lookup"><span data-stu-id="118c2-116">12</span></span>|<span data-ttu-id="118c2-117">예</span><span class="sxs-lookup"><span data-stu-id="118c2-117">Yes</span></span>|  
|<span data-ttu-id="118c2-118">EventSubClass</span><span class="sxs-lookup"><span data-stu-id="118c2-118">EventSubClass</span></span>|`int`|<span data-ttu-id="118c2-119">사용자 정의 분류자 함수의 경우 1입니다.</span><span class="sxs-lookup"><span data-stu-id="118c2-119">1 for the user-defined classifier function.</span></span>|<span data-ttu-id="118c2-120">21</span><span class="sxs-lookup"><span data-stu-id="118c2-120">21</span></span>|<span data-ttu-id="118c2-121">예</span><span class="sxs-lookup"><span data-stu-id="118c2-121">Yes</span></span>|  
|<span data-ttu-id="118c2-122">StartTime</span><span class="sxs-lookup"><span data-stu-id="118c2-122">StartTime</span></span>|`datetime`|<span data-ttu-id="118c2-123">사용자 정의 분류자 함수가 시작되는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="118c2-123">The time when the user-defined classifier function starts.</span></span>|<span data-ttu-id="118c2-124">14</span><span class="sxs-lookup"><span data-stu-id="118c2-124">14</span></span>|<span data-ttu-id="118c2-125">예</span><span class="sxs-lookup"><span data-stu-id="118c2-125">Yes</span></span>|  
|<span data-ttu-id="118c2-126">ObjectID</span><span class="sxs-lookup"><span data-stu-id="118c2-126">ObjectID</span></span>|`int`|<span data-ttu-id="118c2-127">사용자 정의 분류자 개체의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="118c2-127">The ID of the user-defined classifier object.</span></span>|<span data-ttu-id="118c2-128">22</span><span class="sxs-lookup"><span data-stu-id="118c2-128">22</span></span>|<span data-ttu-id="118c2-129">yes</span><span class="sxs-lookup"><span data-stu-id="118c2-129">Yes</span></span>|  
|<span data-ttu-id="118c2-130">ObjectName</span><span class="sxs-lookup"><span data-stu-id="118c2-130">ObjectName</span></span>|`nvarchar(256)`|<span data-ttu-id="118c2-131">분류자 사용자 정의 함수의 두 부분으로 이루어진 이름입니다(예:</span><span class="sxs-lookup"><span data-stu-id="118c2-131">The two-part name of the classifier user-defined function.</span></span> <span data-ttu-id="118c2-132">dbo.classifier).</span><span class="sxs-lookup"><span data-stu-id="118c2-132">For example, dbo.classifier.</span></span>|<span data-ttu-id="118c2-133">34</span><span class="sxs-lookup"><span data-stu-id="118c2-133">34</span></span>|<span data-ttu-id="118c2-134">yes</span><span class="sxs-lookup"><span data-stu-id="118c2-134">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="118c2-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="118c2-135">See Also</span></span>  
 <span data-ttu-id="118c2-136">[확장 이벤트](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="118c2-136">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="118c2-137">[PreConnect: Completed 이벤트 클래스](preconnect-completed-event-class.md) </span><span class="sxs-lookup"><span data-stu-id="118c2-137">[PreConnect:Completed Event Class](preconnect-completed-event-class.md) </span></span>  
 [<span data-ttu-id="118c2-138">리소스 관리자</span><span class="sxs-lookup"><span data-stu-id="118c2-138">Resource Governor</span></span>](../resource-governor/resource-governor.md)  
  
  
