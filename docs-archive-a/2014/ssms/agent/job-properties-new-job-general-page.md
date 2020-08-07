---
title: 작업 속성 및 새 작업 (일반 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7a5d2ab84ed211a03a3c217bd5f4cd54453a4dc5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731331"
---
# <a name="job-properties-and-new-job-general-page"></a><span data-ttu-id="e3a5e-102">작업 속성 및 새 작업(일반 페이지)</span><span class="sxs-lookup"><span data-stu-id="e3a5e-102">Job Properties and New Job (General Page)</span></span>
  <span data-ttu-id="e3a5e-103">이 페이지를 사용 하 여 에이전트 작업의 일반 속성을 확인 하 고 수정할 수 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-103">Use this page to view and modify the general properties of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e3a5e-104">옵션</span><span class="sxs-lookup"><span data-stu-id="e3a5e-104">Options</span></span>  
 <span data-ttu-id="e3a5e-105">**이름**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-105">**Name**</span></span>  
 <span data-ttu-id="e3a5e-106">작업 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-106">Change the name of the job.</span></span>  
  
 <span data-ttu-id="e3a5e-107">**소유자**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-107">**Owner**</span></span>  
 <span data-ttu-id="e3a5e-108">작업의 소유자를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-108">Select the owner for the job.</span></span>  
  
 <span data-ttu-id="e3a5e-109">**범주**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-109">**Category**</span></span>  
 <span data-ttu-id="e3a5e-110">작업의 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-110">Select the job category for the job.</span></span>  
  
 <span data-ttu-id="e3a5e-111">**...**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-111">**...**</span></span>  
 <span data-ttu-id="e3a5e-112">선택한 범주의 작업을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-112">View the jobs in the selected category.</span></span>  
  
 <span data-ttu-id="e3a5e-113">**설명**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-113">**Description**</span></span>  
 <span data-ttu-id="e3a5e-114">작업 설명을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-114">Change the description of the job.</span></span>  
  
 <span data-ttu-id="e3a5e-115">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-115">**Enabled**</span></span>  
 <span data-ttu-id="e3a5e-116">작업을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-116">Enable the job.</span></span> <span data-ttu-id="e3a5e-117">작업을 설정하지 않은 경우 일정 또는 경고에 따라 작업이 실행되지는 않지만 **sp_start_job** 저장 프로시저를 사용하여 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-117">When the job is not enabled, the job does not run in response to a schedule or an alert, although you can still start the job using the **sp_start_job** stored procedure.</span></span>  
  
 <span data-ttu-id="e3a5e-118">**원본**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-118">**Source**</span></span>  
 <span data-ttu-id="e3a5e-119">작업에 사용되는 마스터 서버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-119">Displays the master server for the job.</span></span> <span data-ttu-id="e3a5e-120">**작업 속성 일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-120">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="e3a5e-121">**만든 날짜**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-121">**Created**</span></span>  
 <span data-ttu-id="e3a5e-122">작업을 만든 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-122">Displays the date and time that the job was created.</span></span> <span data-ttu-id="e3a5e-123">**작업 속성 일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-123">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="e3a5e-124">**마지막으로 수정한 날짜**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-124">**Last modified**</span></span>  
 <span data-ttu-id="e3a5e-125">작업을 마지막으로 수정한 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-125">Displays the date and time that the job was last modified.</span></span> <span data-ttu-id="e3a5e-126">**작업 속성 일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-126">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="e3a5e-127">**마지막으로 실행한 날짜**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-127">**Last executed**</span></span>  
 <span data-ttu-id="e3a5e-128">마지막으로 작업 실행을 시작한 날짜 및 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-128">Displays the date and time that the job last started running.</span></span> <span data-ttu-id="e3a5e-129">**작업 속성 일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-129">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
 <span data-ttu-id="e3a5e-130">**작업 기록 보기**</span><span class="sxs-lookup"><span data-stu-id="e3a5e-130">**View Job History**</span></span>  
 <span data-ttu-id="e3a5e-131">작업의 기록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-131">View the job history for the job.</span></span> <span data-ttu-id="e3a5e-132">**작업 속성 일반** 페이지에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3a5e-132">Only available on the **Job PropertiesGeneral** page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a5e-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3a5e-133">See Also</span></span>  
 <span data-ttu-id="e3a5e-134">[작업 구현](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="e3a5e-134">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="e3a5e-135">작업 범주: 작업 범주 관리</span><span class="sxs-lookup"><span data-stu-id="e3a5e-135">Job Categories: Manage Job Categories</span></span>](job-categories-manage-job-categories.md)  
  
  
