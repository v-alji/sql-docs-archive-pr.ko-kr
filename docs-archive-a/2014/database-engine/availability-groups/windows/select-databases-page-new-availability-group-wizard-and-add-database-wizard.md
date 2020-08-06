---
title: 데이터베이스 선택 페이지 (새 가용성 그룹 마법사-데이터베이스 추가 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.adddatabasewizard.selectdatabases.f1
- sql12.swb.newagwizard.selectdatabases.f1
ms.assetid: 929c5e15-d087-438d-b1f2-aa97c5f8bff8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c626b8f0953f18a6dd4661124a09b7f542caeb82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740474"
---
# <a name="select-databases-page-new-availability-group-wizard-add-database-wizard"></a><span data-ttu-id="b70a2-102">Select Databases Page (New Availability Group Wizard-Add Database Wizard)</span><span class="sxs-lookup"><span data-stu-id="b70a2-102">Select Databases Page (New Availability Group Wizard-Add Database Wizard)</span></span>
  <span data-ttu-id="b70a2-103"> 이 도움말 항목에서는 **데이터베이스 지정** 페이지의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-103">This help topic describes the options of the **Specify Databases** page.</span></span> <span data-ttu-id="b70a2-104">이 항목은 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] 의 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 및 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-104">This topic applies to the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
##  <a name="select-databases-options"></a><a name="PageOptions"></a> <span data-ttu-id="b70a2-105">데이터베이스 선택 옵션</span><span class="sxs-lookup"><span data-stu-id="b70a2-105">Select Databases Options</span></span>  
 <span data-ttu-id="b70a2-106">**이 SQL Server 인스턴스의 사용자 데이터베이스 선택** 표에는 모든 로컬 사용자 데이터베이스가 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-106">The **User databases on this instance of SQL Server** grid lists every local user database.</span></span> <span data-ttu-id="b70a2-107">열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-107">The columns are as follows:</span></span>  
  
 <span data-ttu-id="b70a2-108">**이름**</span><span class="sxs-lookup"><span data-stu-id="b70a2-108">**Name**</span></span>  
 <span data-ttu-id="b70a2-109">로컬 사용자 데이터베이스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-109">Displays the name of a local user database.</span></span>  
  
 <span data-ttu-id="b70a2-110">**크기**</span><span class="sxs-lookup"><span data-stu-id="b70a2-110">**Size**</span></span>  
 <span data-ttu-id="b70a2-111">마법사에서 사용할 수 있는 데이터베이스 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-111">Displays the database size, if the size is available to the wizard.</span></span>  
  
 <span data-ttu-id="b70a2-112">**상태**</span><span class="sxs-lookup"><span data-stu-id="b70a2-112">**Status**</span></span>  
 <span data-ttu-id="b70a2-113">지정된 데이터베이스가 가용성 그룹에 추가하기 위한 사전 요구 사항을 충족하는지 여부를 나타내는 텍스트가 있는 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-113">Displays a hyperlink whose text that indicates whether a given database meets the prerequisites for being added to an availability group.</span></span> <span data-ttu-id="b70a2-114">상태가 "**사전 요구 사항 일치**"인 경우 데이터베이스를 가용성 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-114">If the status is "**Meets prerequisites**" you can add the database to the availability group.</span></span> <span data-ttu-id="b70a2-115">데이터베이스가 모든 사전 요구 사항을 충족하지 않는 경우 **상태** 하이퍼링크에 데이터베이스를 사용할 수 없는 이유에 대한 간략한 설명이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-115">If a database does not meet all of the prerequisites, the **Status** hyperlink provides a brief explanation of why the database is ineligible.</span></span> <span data-ttu-id="b70a2-116">자세한 내용을 보려면 하이퍼링크를 클릭하세요.</span><span class="sxs-lookup"><span data-stu-id="b70a2-116">For more information, click the hyperlink.</span></span>  
  
 <span data-ttu-id="b70a2-117">사전 요구 사항을 충족하기 위해 데이터베이스에서 작업을 수행하는 동안 **데이터베이스 선택** 페이지에서 마법사를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-117">You can leave the wizard on the **Select Database** page while you take action on a database to meet a prerequisite.</span></span> <span data-ttu-id="b70a2-118">**데이터베이스 선택** 페이지로 돌아가서 **새로 고침** 을 클릭하여 표를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-118">When you return to the **Select Databases** page, click **Refresh** to update the grid.</span></span>  
  
 <span data-ttu-id="b70a2-119">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="b70a2-119">**Refresh**</span></span>  
 <span data-ttu-id="b70a2-120">표를 새로 고치려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-120">Click to refresh the grid.</span></span> <span data-ttu-id="b70a2-121">이 기능은 사전 요구 사항을 충족하기 위해 데이터베이스에서 작업을 수행한 이후에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b70a2-121">This is useful after you take action on a database to meet a prerequisite.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b70a2-122">관련 작업</span><span class="sxs-lookup"><span data-stu-id="b70a2-122">Related Tasks</span></span>  
  
-   [<span data-ttu-id="b70a2-123">새 가용성 그룹 대화 상자 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b70a2-123">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="b70a2-124">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="b70a2-124">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="b70a2-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b70a2-125">See Also</span></span>  
 <span data-ttu-id="b70a2-126">[AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b70a2-126">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="b70a2-127">AlwaysOn 가용성 그룹 &#40;SQL Server에 대 한 필수 조건, 제한 사항 및 권장 사항&#41;</span><span class="sxs-lookup"><span data-stu-id="b70a2-127">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
