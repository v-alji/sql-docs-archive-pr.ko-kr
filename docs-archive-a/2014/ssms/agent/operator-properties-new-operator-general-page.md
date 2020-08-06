---
title: 운영자 속성 및 새 운영자 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ffd4a604275153a2bfe7071c442cc110815f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649326"
---
# <a name="operator-properties-and-new-operator-general-page"></a><span data-ttu-id="2552a-102">운영자 속성 및 새 운영자(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="2552a-102">Operator Properties and New Operator (General Page)</span></span>
  <span data-ttu-id="2552a-103">이 페이지를 사용 하 여 에이전트 운영자의 일반 속성을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span>  
  
## <a name="options"></a><span data-ttu-id="2552a-104">옵션</span><span class="sxs-lookup"><span data-stu-id="2552a-104">Options</span></span>  
 <span data-ttu-id="2552a-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="2552a-105">**Name**</span></span>  
 <span data-ttu-id="2552a-106">운영자의 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-106">Change the name of the operator.</span></span>  
  
 <span data-ttu-id="2552a-107">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="2552a-107">**Enabled**</span></span>  
 <span data-ttu-id="2552a-108">운영자를 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-108">Enable the operator.</span></span> <span data-ttu-id="2552a-109">활성화하지 않으면 해당 운영자에게 알림이 전송되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-109">When not enabled, no notifications are sent to the operator.</span></span>  
  
 <span data-ttu-id="2552a-110">**전자 메일 이름**</span><span class="sxs-lookup"><span data-stu-id="2552a-110">**E-mail name**</span></span>  
 <span data-ttu-id="2552a-111">운영자의 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-111">Specifies the e-mail address for the operator.</span></span>  
  
 <span data-ttu-id="2552a-112">**Net Send 주소**</span><span class="sxs-lookup"><span data-stu-id="2552a-112">**Net send address**</span></span>  
 <span data-ttu-id="2552a-113">**net send**에 사용할 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-113">Specify the address to use for **net send**.</span></span>  
  
 <span data-ttu-id="2552a-114">**호출기 전자 메일 이름**</span><span class="sxs-lookup"><span data-stu-id="2552a-114">**Pager e-mail name**</span></span>  
 <span data-ttu-id="2552a-115">운영자의 호출기에 사용할 전자 메일 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-115">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
 <span data-ttu-id="2552a-116">**호출기 연락 가능 근무 일정**</span><span class="sxs-lookup"><span data-stu-id="2552a-116">**Pager on duty schedule**</span></span>  
 <span data-ttu-id="2552a-117">호출기로 연락 가능한 시간을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-117">Sets the times at which the pager is active.</span></span>  
  
 <span data-ttu-id="2552a-118">**월요일 - 일요일**</span><span class="sxs-lookup"><span data-stu-id="2552a-118">**Monday - Sunday**</span></span>  
 <span data-ttu-id="2552a-119">호출기로 연락 가능한 요일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-119">Select the days that the pager is active.</span></span>  
  
 <span data-ttu-id="2552a-120">**업무 시작 시간**</span><span class="sxs-lookup"><span data-stu-id="2552a-120">**Workday begin**</span></span>  
 <span data-ttu-id="2552a-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 호출기로 메시지를 보내기 시작하는 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-121">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
 <span data-ttu-id="2552a-122">**업무 종료 시간**</span><span class="sxs-lookup"><span data-stu-id="2552a-122">**Workday end**</span></span>  
 <span data-ttu-id="2552a-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트에서 호출기로 메시지를 더 이상 보내지 않는 기준 시간을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="2552a-123">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2552a-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2552a-124">See Also</span></span>  
 [<span data-ttu-id="2552a-125">연산자</span><span class="sxs-lookup"><span data-stu-id="2552a-125">Operators</span></span>](operators.md)  
  
  
