---
title: 일정 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6fa18d620d630484815966372d5de83bb52e8caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649345"
---
# <a name="manage-schedules"></a><span data-ttu-id="4dada-102">일정 관리</span><span class="sxs-lookup"><span data-stu-id="4dada-102">Manage Schedules</span></span>
  <span data-ttu-id="4dada-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]에이전트 작업 일정의 속성을 보고 변경할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4dada-103">Allows you to view and change properties for [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job schedules.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4dada-104">옵션</span><span class="sxs-lookup"><span data-stu-id="4dada-104">Options</span></span>  
 <span data-ttu-id="4dada-105">**사용 가능한 일정**</span><span class="sxs-lookup"><span data-stu-id="4dada-105">**Available schedules**</span></span>  
 <span data-ttu-id="4dada-106">이 사용자가 사용할 수 있는 일정을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-106">Lists the schedules available for this user.</span></span> <span data-ttu-id="4dada-107">작업 및 일정은 소유자가 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-107">Notice that a job and a schedule must have the same owner.</span></span> <span data-ttu-id="4dada-108">따라서 이 목록에는 작업의 소유자가 소유한 일정만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-108">Therefore, this list only includes schedules owned by the owner of the job.</span></span>  
  
 <span data-ttu-id="4dada-109">**이름**</span><span class="sxs-lookup"><span data-stu-id="4dada-109">**Name**</span></span>  
 <span data-ttu-id="4dada-110">일정 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-110">Displays the name of the schedule.</span></span>  
  
 <span data-ttu-id="4dada-111">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="4dada-111">**Enabled**</span></span>  
 <span data-ttu-id="4dada-112">일정을 사용하려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-112">Select this option to enable the schedule.</span></span>  
  
 <span data-ttu-id="4dada-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="4dada-113">**Description**</span></span>  
 <span data-ttu-id="4dada-114">일정에서 작업을 실행하는 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-114">Describes the conditions under which the schedule runs the job.</span></span>  
  
 <span data-ttu-id="4dada-115">**이 일정 내의 작업**</span><span class="sxs-lookup"><span data-stu-id="4dada-115">**Jobs in schedule**</span></span>  
 <span data-ttu-id="4dada-116">일정에 연결된 작업 번호를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-116">Lists the job numbers attached to the schedule.</span></span> <span data-ttu-id="4dada-117">작업의 속성을 보려면 번호를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-117">Click a number to view the properties of the job.</span></span>  
  
 <span data-ttu-id="4dada-118">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="4dada-118">**New**</span></span>  
 <span data-ttu-id="4dada-119">새 일정을 만들려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-119">Click this button to create a new schedule.</span></span>  
  
 <span data-ttu-id="4dada-120">**삭제**</span><span class="sxs-lookup"><span data-stu-id="4dada-120">**Delete**</span></span>  
 <span data-ttu-id="4dada-121">선택한 일정을 삭제하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-121">Click this button to delete the selected schedule.</span></span>  
  
 <span data-ttu-id="4dada-122">**속성**</span><span class="sxs-lookup"><span data-stu-id="4dada-122">**Properties**</span></span>  
 <span data-ttu-id="4dada-123">선택한 일정의 속성을 변경하려면 이 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4dada-123">Click this button to change the properties of the selected schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dada-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4dada-124">See Also</span></span>  
 [<span data-ttu-id="4dada-125">일정을 만들고 작업에 연결</span><span class="sxs-lookup"><span data-stu-id="4dada-125">Create and Attach Schedules to Jobs</span></span>](create-and-attach-schedules-to-jobs.md)  
  
  
