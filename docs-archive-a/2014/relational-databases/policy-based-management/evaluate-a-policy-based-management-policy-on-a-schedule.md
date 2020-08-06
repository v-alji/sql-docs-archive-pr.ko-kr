---
title: 일정에 따라 정책 기반 관리 정책 평가 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, evaluate policy
ms.assetid: bea09522-ff47-4037-ab55-a98ea7c10099
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f1c6b1a7d13d14c02f4b4e537c2dbdb2df39d02c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731515"
---
# <a name="evaluate-a-policy-based-management-policy-on-a-schedule"></a><span data-ttu-id="fa52d-102">일정에 따라 정책 기반 관리 정책 평가</span><span class="sxs-lookup"><span data-stu-id="fa52d-102">Evaluate a Policy-Based Management Policy on a Schedule</span></span>
  <span data-ttu-id="fa52d-103">이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 일정에 따라 정책 기반 관리 정책을 평가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-103">This topic describes how to evaluate a Policy-Based Management policy on a schedule in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="fa52d-104">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fa52d-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fa52d-105">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fa52d-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fa52d-106">보안</span><span class="sxs-lookup"><span data-stu-id="fa52d-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="fa52d-107">**다음을 사용하여 일정에 따라 정책을 평가하려면:**</span><span class="sxs-lookup"><span data-stu-id="fa52d-107">**To evaluate a policy on a schedule, using:**</span></span>  
  
     [<span data-ttu-id="fa52d-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fa52d-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fa52d-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fa52d-109">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fa52d-110">보안</span><span class="sxs-lookup"><span data-stu-id="fa52d-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fa52d-111">권한</span><span class="sxs-lookup"><span data-stu-id="fa52d-111">Permissions</span></span>  
 <span data-ttu-id="fa52d-112">msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-112">Requires membership in the PolicyAdministratorRole role in the msdb database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fa52d-113">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fa52d-113">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-evaluate-a-policy-on-a-schedule"></a><span data-ttu-id="fa52d-114">일정에 따라 정책을 평가하려면</span><span class="sxs-lookup"><span data-stu-id="fa52d-114">To evaluate a policy on a schedule</span></span>  
  
1.  <span data-ttu-id="fa52d-115">**개체 탐색기**에서 더하기 기호를 클릭하여 평가하려는 정책 일정이 들어 있는 서버를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-115">In **Object Explorer**, click the plus sign to expand the server that contains the policy schedule that you want to evaluate.</span></span>  
  
2.  <span data-ttu-id="fa52d-116">더하기 기호를 클릭하여 **관리** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-116">Click the plus sign to expand the **Management** folder.</span></span>  
  
3.  <span data-ttu-id="fa52d-117">더하기 기호를 클릭하여 **정책 관리**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-117">Click the plus sign to expand **Policy Management**.</span></span>  
  
4.  <span data-ttu-id="fa52d-118">더하기 기호를 클릭하여 **정책** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-118">Click the plus sign to expand the **Policies** folder.</span></span>  
  
5.  <span data-ttu-id="fa52d-119">평가하려는 일정이 지정된 정책을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-119">Right-click the policy whose schedule you what to evaluate and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="fa52d-120">**정책 열기** _–policy_name_ 대화 상자의 **평가 모드** 목록에서 **예약 시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-120">On the **Open Policy -**_policy_name_ dialog box, in the **Evaluation Mode** list, select **On schedule**.</span></span>  
  
7.  <span data-ttu-id="fa52d-121">**일정**에서 **선택** 을 클릭하여 기존 일정을 지정하거나 **새로 만들기** 를 클릭하여 새 일정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-121">Under **Schedule**, click either **Pick** to specify an existing schedule or **New** to create a new schedule.</span></span>  
  
8.  <span data-ttu-id="fa52d-122">완료되었으면 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa52d-122">When finished, click **OK**.</span></span>  
  
  
