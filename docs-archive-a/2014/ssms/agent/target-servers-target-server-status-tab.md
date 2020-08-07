---
title: 대상 서버(대상 서버 상태 탭) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.target.status.f1
ms.assetid: 010a4cab-d878-4889-8ac8-7d91db6345d6
author: stevestein
ms.author: sstein
ms.openlocfilehash: be51648a4642d25c59e52be65e43037844ec0909
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731315"
---
# <a name="target-servers-target-server-status-tab"></a><span data-ttu-id="e2f58-102">대상 서버(대상 서버 상태 탭)</span><span class="sxs-lookup"><span data-stu-id="e2f58-102">Target Servers (Target Server Status Tab)</span></span>
  <span data-ttu-id="e2f58-103">이 페이지를 사용하여 이 마스터 서버와 관련된 대상 서버의 상태를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-103">Use this page to view the status of the target servers for this master server.</span></span>  
  
## <a name="options"></a><span data-ttu-id="e2f58-104">옵션</span><span class="sxs-lookup"><span data-stu-id="e2f58-104">Options</span></span>  
 <span data-ttu-id="e2f58-105">**대상 서버**</span><span class="sxs-lookup"><span data-stu-id="e2f58-105">**Target Server**</span></span>  
 <span data-ttu-id="e2f58-106">대상 서버의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-106">View the name of the target server.</span></span>  
  
 <span data-ttu-id="e2f58-107">**현지 시간**</span><span class="sxs-lookup"><span data-stu-id="e2f58-107">**Local time**</span></span>  
 <span data-ttu-id="e2f58-108">대상 서버의 현지 표준 시간대를 기준으로 해당 서버의 날짜 및 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-108">View the date and time of the target server in the local time zone for that server.</span></span>  
  
 <span data-ttu-id="e2f58-109">**마지막 폴링**</span><span class="sxs-lookup"><span data-stu-id="e2f58-109">**Last polled**</span></span>  
 <span data-ttu-id="e2f58-110">대상 서버가 마지막으로 마스터 서버를 폴링한 로컬 날짜와 시간을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-110">View the local date and time that the target server last polled the master.</span></span>  
  
 <span data-ttu-id="e2f58-111">**읽지 않은 명령**</span><span class="sxs-lookup"><span data-stu-id="e2f58-111">**Unread instructions**</span></span>  
 <span data-ttu-id="e2f58-112">대상 서버가 아직 받지 못한 명령 수를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-112">View the number of instructions that the target server has not yet received.</span></span>  
  
 <span data-ttu-id="e2f58-113">**상태**</span><span class="sxs-lookup"><span data-stu-id="e2f58-113">**Status**</span></span>  
 <span data-ttu-id="e2f58-114">대상 서버의 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-114">View the status of the target server.</span></span>  
  
 <span data-ttu-id="e2f58-115">**강제 폴링**</span><span class="sxs-lookup"><span data-stu-id="e2f58-115">**Force Poll**</span></span>  
 <span data-ttu-id="e2f58-116">이 단추를 클릭하면 대상 서버가 마스터 서버에 폴링을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-116">Click this button to force the selected target servers to poll the master server.</span></span>  
  
 <span data-ttu-id="e2f58-117">**강제 제거**</span><span class="sxs-lookup"><span data-stu-id="e2f58-117">**Force Defection**</span></span>  
 <span data-ttu-id="e2f58-118">이 단추를 클릭하면 대상 서버가 마스터 서버에서 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-118">Click this button to force the selected target servers to defect from the master server.</span></span>  
  
 <span data-ttu-id="e2f58-119">**명령 게시**</span><span class="sxs-lookup"><span data-stu-id="e2f58-119">**Post Instructions**</span></span>  
 <span data-ttu-id="e2f58-120">선택한 대상 서버에 명령을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-120">Post instructions to the selected target servers.</span></span>  
  
 <span data-ttu-id="e2f58-121">**자동 새로 고침 설정**</span><span class="sxs-lookup"><span data-stu-id="e2f58-121">**Enable Auto Refresh**</span></span>  
 <span data-ttu-id="e2f58-122">화면의 정보를 자동으로 새로 고치려면 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-122">Select this option to automatically refresh the information shown.</span></span>  
  
 <span data-ttu-id="e2f58-123">**새로 고침 간격**</span><span class="sxs-lookup"><span data-stu-id="e2f58-123">**Refresh every**</span></span>  
 <span data-ttu-id="e2f58-124">페이지의 정보를 새로 고치는 주기를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e2f58-124">Specify how often the information on this page is refreshed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f58-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2f58-125">See Also</span></span>  
 [<span data-ttu-id="e2f58-126">기업 내 관리 자동화</span><span class="sxs-lookup"><span data-stu-id="e2f58-126">Automated Administration Across an Enterprise</span></span>](automated-administration-across-an-enterprise.md)  
  
  
