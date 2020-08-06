---
title: SQL 스크립트 생성(복제 개체) | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.generatesqlscript.f1
helpviewer_keywords:
- Generate SQL Script dialog box
ms.assetid: b7ccc34e-1c22-44b8-8eb5-f6423af3164e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 31a4b318eb3a4c0e5d9f79f43efdcf97c42957f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646884"
---
# <a name="generate-sql-script-replication-objects"></a><span data-ttu-id="d958a-102">SQL 스크립트 생성(복제 개체)</span><span class="sxs-lookup"><span data-stu-id="d958a-102">Generate SQL Script (Replication Objects)</span></span>
  <span data-ttu-id="d958a-103">복제 스크립트에는 게시 또는 구독과 같이 스크립팅된 복제 구성 요소를 구현하는 데 필요한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 저장 프로시저가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-103">A replication script contains the [!INCLUDE[tsql](../../includes/tsql-md.md)] system stored procedures necessary to implement the replication components scripted, such as a publication or subscription.</span></span> <span data-ttu-id="d958a-104">토폴로지의 모든 복제 구성 요소는 재해 복구 계획의 일부로 스크립팅되어야 하며 반복 태스크를 자동화하는 데도 스크립트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-104">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="d958a-105">복제에서는 복제 개체를 스크립팅할 수 있는 다음 두 개의 대화 상자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-105">Replication offers two dialog boxes for scripting replication objects:</span></span>  
  
-   <span data-ttu-id="d958a-106">**SQL 스크립트 생성**대화 상자 - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 있는 **복제**폴더 및 모든 하위 폴더의 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-106">**Generate SQL Script**, which is available from the context menu of the **Replication** folder and all subfolders in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d958a-107">이 대화 상자를 사용하여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 복제 개체를 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-107">This dialog box allows you to script all replication objects on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="d958a-108">**SQL 스크립트 생성 \<ObjectName>** - 게시 및 구독의 상황에 맞는 메뉴에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-108">**Generate SQL Script \<ObjectName>**, which is available from the context menu for publications and subscriptions.</span></span> <span data-ttu-id="d958a-109">이 대화 상자를 사용하여 개별 개체를 스크립팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-109">This dialog box allows you to script individual objects.</span></span>  
  
 <span data-ttu-id="d958a-110">이러한 대화 상자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 단일 인스턴스에 있는 개체를 스크립팅하며, 다른 인스턴스에 연결하여 관련 개체를 스크립팅하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-110">These dialog boxes script objects on a single instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; they do not connect to other instances to script related objects.</span></span>  
  
## <a name="generate-sql-script-options"></a><span data-ttu-id="d958a-111">SQL 스크립트 생성 옵션</span><span class="sxs-lookup"><span data-stu-id="d958a-111">Generate SQL Script Options</span></span>  
 <span data-ttu-id="d958a-112">**배포자 속성**</span><span class="sxs-lookup"><span data-stu-id="d958a-112">**Distributor properties**</span></span>  
 <span data-ttu-id="d958a-113">저장 프로시저를 스크립팅하여 배포자를 설정 또는 해제하고, 배포자와 연결된 게시자를 추가 또는 삭제하고, 배포 데이터베이스를 생성 또는 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-113">Select to script stored procedures to: enable or disable the Distributor; add or drop Publishers associated with the Distributor; and create or drop the distribution database.</span></span>  
  
 <span data-ttu-id="d958a-114">**다음 데이터 원본의 게시**</span><span class="sxs-lookup"><span data-stu-id="d958a-114">**Publications in the following data sources**</span></span>  
 <span data-ttu-id="d958a-115">저장 프로시저를 스크립팅하여 게시를 설정 또는 해제하고, 아티클, 밀어넣기 구독 및 복제 작업을 생성 또는 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-115">Select to script stored procedures to: enable or disable publishing; and create or drop publications, articles, push subscriptions, and replication jobs.</span></span>  
  
 <span data-ttu-id="d958a-116">**다음 데이터 원본의 구독**</span><span class="sxs-lookup"><span data-stu-id="d958a-116">**Subscriptions in the following data sources**</span></span>  
 <span data-ttu-id="d958a-117">저장 프로시저를 스크립팅하여 끌어오기 구독 및 복제 작업을 생성 또는 삭제하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-117">Select to script stored procedures to create or drop pull subscriptions and replication jobs.</span></span>  
  
 <span data-ttu-id="d958a-118">**구성 요소 생성 또는 선택** 및 **구성 요소 삭제 또는 해제**</span><span class="sxs-lookup"><span data-stu-id="d958a-118">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="d958a-119">복제 개체를 생성 또는 삭제하는 명령을 스크립트에 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-119">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d958a-120">에서는 대화 상자를 사용하여 구성 요소를 설정 및 해제하는 스크립트 집합을 만들 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-120">recommends that you use the dialog box to create a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="d958a-121">**복제 작업**</span><span class="sxs-lookup"><span data-stu-id="d958a-121">**Replication jobs**</span></span>  
 <span data-ttu-id="d958a-122">저장 프로시저 호출과 함께 복제 작업을 스크립팅하려면 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-122">Select to script replication jobs in addition to stored procedure calls.</span></span> <span data-ttu-id="d958a-123">이 옵션은 배포자에서 스크립팅하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-123">This option is available only when scripting from a Distributor.</span></span>  
  
 <span data-ttu-id="d958a-124">복제 저장 프로시저는 실행될 때 필요한 작업을 만들기 때문에 이 옵션을 선택할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-124">Replication stored procedures create the necessary jobs when they are executed, so it is not required to select this option.</span></span> <span data-ttu-id="d958a-125">그러나 개별 작업을 다시 만들어야 하는 경우 작업 레코드를 만들어 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-125">However, it can be useful to have a record of the jobs created in case an individual job must be recreated.</span></span>  
  
## <a name="generate-sql-script-objectname-options"></a><span data-ttu-id="d958a-126">SQL 스크립트 생성 \<ObjectName> 옵션</span><span class="sxs-lookup"><span data-stu-id="d958a-126">Generate SQL Script \<ObjectName> Options</span></span>  
 <span data-ttu-id="d958a-127">**구성 요소 생성 또는 선택** 및 **구성 요소 삭제 또는 해제**</span><span class="sxs-lookup"><span data-stu-id="d958a-127">**To create or enable the components** and **To drop or disable the components**</span></span>  
 <span data-ttu-id="d958a-128">복제 개체를 생성 또는 삭제하는 명령을 스크립트에 포함할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-128">Specify whether the script should include commands for creating or dropping a replication object.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="d958a-129">에서는 대화 상자를 사용하여 구성 요소를 설정 및 해제하는 스크립트 집합을 만들 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-129">recommends that you use the dialog box, creating a set of scripts for enabling and disabling components.</span></span>  
  
 <span data-ttu-id="d958a-130">**복제 작업**</span><span class="sxs-lookup"><span data-stu-id="d958a-130">**Replication jobs**</span></span>  
 <span data-ttu-id="d958a-131">이 옵션은 **SQL 스크립트 생성** 대화 상자에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d958a-131">This option is available only from the **Generate SQL Script** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d958a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d958a-132">See Also</span></span>  
 [<span data-ttu-id="d958a-133">복제 스크립팅</span><span class="sxs-lookup"><span data-stu-id="d958a-133">Scripting Replication</span></span>](scripting-replication.md)  
  
  
