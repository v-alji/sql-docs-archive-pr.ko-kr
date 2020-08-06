---
title: 템플릿을 사용하여 리소스 관리자 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, templates
ms.assetid: f342dec2-d1d6-483e-b44e-98eb7d168b5e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 62edb23cf55a953cb0fef54f002f8eaaa16f58ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659933"
---
# <a name="configure-resource-governor-using-a-template"></a><span data-ttu-id="742c7-102">템플릿을 사용하여 리소스 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="742c7-102">Configure Resource Governor Using a Template</span></span>
  <span data-ttu-id="742c7-103">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 제공된 템플릿을 사용하여 리소스 관리자를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-103">You can configure Resource Governor by using a template that is provided in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="742c7-104">**시작하기 전 주의 사항:**  [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="742c7-104">**Before you begin:**  [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="742c7-105">**작업 그룹을 만들려면** [템플릿](#ConfRGTemplate)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-105">**To create a workload group, using:**  [a template](#ConfRGTemplate)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="742c7-106">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="742c7-106">Before You Begin</span></span>  
 <span data-ttu-id="742c7-107">다음 단계에 따라 리소스 풀과 해당 리소스 풀의 작업 그룹을 만드는 템플릿을 열고 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-107">Use the following steps to open and modify a template that creates a resource pool and a workload group for the pool.</span></span> <span data-ttu-id="742c7-108">또한 이 템플릿을 사용하여 새 연결을 기본 그룹 또는 만든 작업 그룹으로 라우팅하는 분류자 사용자 정의 함수를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-108">In addition, this template enables you to create a classifier user-defined function that routes new connections to either the default group or the workload group that you create.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="742c7-109">권한</span><span class="sxs-lookup"><span data-stu-id="742c7-109">Permissions</span></span>  
 <span data-ttu-id="742c7-110">템플릿에서 리소스 관리자 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하려면 CONTROL SERVER 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-110">The resource governor [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the template require CONTROL SERVER permission.</span></span>  
  
##  <a name="configure-resource-governor-using-a-template"></a><a name="ConfRGTemplate"></a> <span data-ttu-id="742c7-111">템플릿을 사용하여 리소스 관리자 구성</span><span class="sxs-lookup"><span data-stu-id="742c7-111">Configure Resource Governor Using a Template</span></span>  
 <span data-ttu-id="742c7-112">**다음에서 템플릿을 사용하여 리소스 관리자를 구성하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="742c7-112">**To configure resource governor by using a template in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**</span></span>  
  
1.  <span data-ttu-id="742c7-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="742c7-114">**템플릿 탐색기**에서 **리소스 관리자**를 확장한 다음 **리소스 관리자 구성**을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-114">In **Template Explorer**, expand **Resource Governor**, and then double-click **Configure Resource Governor**.</span></span>  
  
3.  <span data-ttu-id="742c7-115">**데이터베이스 엔진에 연결**에 필요한 정보를 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-115">In **Connect to Database Engine**, enter the required information, and then click **OK**.</span></span> <span data-ttu-id="742c7-116">쿼리 편집기에 Configure Resource Governor.sql 템플릿이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-116">The template Configure Resource Governor.sql is provided in the Query Editor.</span></span> <span data-ttu-id="742c7-117">이 템플릿을 사용하여 리소스 풀, 작업 그룹 및 분류자 함수를 만들고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-117">Use this template to create and configure a resource pool, a workload group, and a classifier function.</span></span>  
  
4.  <span data-ttu-id="742c7-118">템플릿의 값을 변경하려면 Ctrl+Shift+M을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-118">To change the values in the template, press CTRL+SHIFT+M.</span></span> <span data-ttu-id="742c7-119">**템플릿 매개 변수 값 지정** 창에 사용할 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-119">In the **Specify Values for Template Parameters** window, enter the values that you want to use.</span></span>  
  
5.  <span data-ttu-id="742c7-120">템플릿의 변경 내용을 저장하려면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-120">To save the changes that you make to the template, click **OK**.</span></span>  
  
6.  <span data-ttu-id="742c7-121">쿼리를 실행하려면 **실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="742c7-121">To run the query, click **Execute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742c7-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="742c7-122">See Also</span></span>  
 <span data-ttu-id="742c7-123">[리소스 관리자](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-123">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="742c7-124">[리소스 관리자 사용](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-124">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="742c7-125">[리소스 관리자 리소스 풀](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-125">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="742c7-126">[리소스 관리자 작업 그룹](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-126">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="742c7-127">[리소스 관리자 분류자 함수](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-127">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="742c7-128">[리소스 관리자 속성 보기](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="742c7-128">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="742c7-129">[CREATE RESOURCE POOL&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="742c7-129">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="742c7-130">[CREATE WORKLOAD GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="742c7-130">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="742c7-131">[CREATE FUNCTION&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="742c7-131">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="742c7-132">ALTER RESOURCE GOVERNOR&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="742c7-132">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
