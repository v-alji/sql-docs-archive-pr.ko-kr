---
title: 기존 보조 복제본 페이지에 연결 (복제본 추가 마법사 및 데이터베이스 추가 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.connecttoreplicas.f1
- sql12.swb.adddatabasewizard.connecttoreplicas.f1
ms.assetid: 850f1bc8-d7d0-425c-bd7b-03f0e9d3348e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 80af8dfebd6e23a923ddf67438edabf9ab0e2f65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729828"
---
# <a name="connect-to-existing-secondary-replicas-page-add-replica-wizard-and-add-databases-wizard"></a><span data-ttu-id="39206-102">기존 보조 복제본 페이지로 연결(복제본 추가 마법사 및 데이터베이스 추가 마법사)</span><span class="sxs-lookup"><span data-stu-id="39206-102">Connect to Existing Secondary Replicas Page (Add Replica Wizard and Add Databases Wizard)</span></span>
  <span data-ttu-id="39206-103"> 이 도움말 항목에서는 **기존 보조 복제본에 연결** 페이지의 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-103">This help topic describes the options of the **Connect to Existing Secondary Replicas** page.</span></span> <span data-ttu-id="39206-104">이 항목은 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 의 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] 와 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39206-104">This topic is used by the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] and [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="39206-105">**표 열:**</span><span class="sxs-lookup"><span data-stu-id="39206-105">**Grid columns:**</span></span>  
 <span data-ttu-id="39206-106">**서버 인스턴스**</span><span class="sxs-lookup"><span data-stu-id="39206-106">**Server Instance**</span></span>  
 <span data-ttu-id="39206-107">가용성 복제본을 호스팅할 서버 인스턴스의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-107">Displays the name of the server instance that will host the availability replica.</span></span>  
  
 <span data-ttu-id="39206-108">**다음 계정으로 연결**</span><span class="sxs-lookup"><span data-stu-id="39206-108">**Connected As**</span></span>  
 <span data-ttu-id="39206-109">연결이 설정된 후에 서버 인스턴스에 연결되는 계정을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-109">Displays the account that is connected to the server instance, once the connection has been established.</span></span> <span data-ttu-id="39206-110">이 열에 지정된 서버 인스턴스에 대해 "**연결되지 않음**"이 표시되는 경우 **연결** 또는 **모든 연결** 단추를 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-110">If this column displays "**Not Connected**" for a given server instance, you will need to click either the **Connect** or **Connect All** button.</span></span>  
  
 <span data-ttu-id="39206-111">**연결**</span><span class="sxs-lookup"><span data-stu-id="39206-111">**Connect**</span></span>  
 <span data-ttu-id="39206-112">이 서버 인스턴스가 연결해야 하는 다른 서버 인스턴스와 다른 계정으로 실행 중인 경우 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-112">Click if this server instance is running under a different account than other server instances to which you need to connect.</span></span>  
  
 <span data-ttu-id="39206-113">**모든 연결**</span><span class="sxs-lookup"><span data-stu-id="39206-113">**Connect All**</span></span>  
 <span data-ttu-id="39206-114">연결해야 하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 의 모든 인스턴스가 같은 사용자 계정의 서비스로 실행 중인 경우에만 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-114">Click only if every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which you need to connect is running as a service in the same user account.</span></span>  
  
 <span data-ttu-id="39206-115">**취소**</span><span class="sxs-lookup"><span data-stu-id="39206-115">**Cancel**</span></span>  
 <span data-ttu-id="39206-116">마법사를 취소하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="39206-116">Click to cancel the wizard.</span></span> <span data-ttu-id="39206-117">**기존 보조 복제본에 연결** 페이지에서 마법사를 취소하면 작업이 수행되지 않고 마법사가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="39206-117">On the **Connect to Existing Secondary Replica** page, cancelling the wizard cause it to exit without performing any actions.</span></span>  
  

  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="39206-118">관련 작업</span><span class="sxs-lookup"><span data-stu-id="39206-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="39206-119">가용성 그룹에 복제본 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="39206-119">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="39206-120">가용성 그룹에 데이터베이스 추가 마법사 사용&#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="39206-120">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  

  
## <a name="see-also"></a><span data-ttu-id="39206-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="39206-121">See Also</span></span>  
 [<span data-ttu-id="39206-122">AlwaysOn 가용성 그룹 &#40;SQL Server 개요&#41;</span><span class="sxs-lookup"><span data-stu-id="39206-122">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
