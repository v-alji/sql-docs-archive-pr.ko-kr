---
title: 중단점 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.setbreakpoints.f1
helpviewer_keywords:
- Set Breakpoints dialog box
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8115fcd845ee5ff415d13aa4fe36230234e33ca0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738115"
---
# <a name="set-breakpoints"></a><span data-ttu-id="115d7-102">중단점 설정</span><span class="sxs-lookup"><span data-stu-id="115d7-102">Set Breakpoints</span></span>
  <span data-ttu-id="115d7-103">**중단점 설정** 대화 상자를 사용하여 중단점을 설정할 이벤트를 지정하고 중단점의 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-103">Use the **Set Breakpoints** dialog box to specify the events on which to enable breakpoints and to control the behavior of the breakpoint.</span></span>  
  
## <a name="options"></a><span data-ttu-id="115d7-104">옵션</span><span class="sxs-lookup"><span data-stu-id="115d7-104">Options</span></span>  
 <span data-ttu-id="115d7-105">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="115d7-105">**Enabled**</span></span>  
 <span data-ttu-id="115d7-106">이벤트에 중단점을 설정하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-106">Select to enable a breakpoint on an event.</span></span>  
  
 <span data-ttu-id="115d7-107">**Break Condition**</span><span class="sxs-lookup"><span data-stu-id="115d7-107">**Break Condition**</span></span>  
 <span data-ttu-id="115d7-108">중단점을 설정할 사용 가능한 이벤트 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-108">View a list of available events on which to set breakpoints.</span></span>  
  
 <span data-ttu-id="115d7-109">**Hit Count Type**</span><span class="sxs-lookup"><span data-stu-id="115d7-109">**Hit Count Type**</span></span>  
 <span data-ttu-id="115d7-110">중단점이 적용되는 시기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-110">Specify when the breakpoint takes effect.</span></span>  
  
|<span data-ttu-id="115d7-111">값</span><span class="sxs-lookup"><span data-stu-id="115d7-111">Value</span></span>|<span data-ttu-id="115d7-112">설명</span><span class="sxs-lookup"><span data-stu-id="115d7-112">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="115d7-113">**항상**</span><span class="sxs-lookup"><span data-stu-id="115d7-113">**Always**</span></span>|<span data-ttu-id="115d7-114">중단점에 도달하면 실행이 항상 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-114">Execution is always suspended when the breakpoint is hit.</span></span>|  
|<span data-ttu-id="115d7-115">**다음과 같은 적중 횟수**</span><span class="sxs-lookup"><span data-stu-id="115d7-115">**Hit count equals**</span></span>|<span data-ttu-id="115d7-116">중단점이 발생한 횟수가 적중 횟수와 같으면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-116">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|  
|<span data-ttu-id="115d7-117">**다음보다 크거나 같은 적중 횟수**</span><span class="sxs-lookup"><span data-stu-id="115d7-117">**Hit greater or equal**</span></span>|<span data-ttu-id="115d7-118">중단점이 발생한 횟수가 적중 횟수보다 크거나 같으면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-118">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|  
|<span data-ttu-id="115d7-119">**다음 배수의 적중 횟수**</span><span class="sxs-lookup"><span data-stu-id="115d7-119">**Hit count multiple**</span></span>|<span data-ttu-id="115d7-120">적중 횟수의 배수가 되면 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-120">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="115d7-121">예를 들어 이 옵션을 5로 설정하면 5번째 중단점마다 실행이 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-121">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|  
  
 <span data-ttu-id="115d7-122">**적중 횟수**</span><span class="sxs-lookup"><span data-stu-id="115d7-122">**Hit Count**</span></span>  
 <span data-ttu-id="115d7-123">중단을 트리거하는 적중 횟수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-123">Specify the number of hits at which to trigger a break.</span></span> <span data-ttu-id="115d7-124">이 옵션은 중단점을 항상 적용하는 경우에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="115d7-124">This option is not available if the breakpoint is always in effect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="115d7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="115d7-125">See Also</span></span>  
 [<span data-ttu-id="115d7-126">제어 흐름 디버깅</span><span class="sxs-lookup"><span data-stu-id="115d7-126">Debugging Control Flow</span></span>](../../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  
