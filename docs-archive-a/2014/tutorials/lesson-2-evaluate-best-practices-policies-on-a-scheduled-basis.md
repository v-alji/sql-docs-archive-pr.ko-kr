---
title: '2 단원: 일정에 따라 최선의 구현 방법 정책 평가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648720"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a><span data-ttu-id="4d40f-102">2단원: 일정에 따라 최선의 구현 방법 정책 평가</span><span class="sxs-lookup"><span data-stu-id="4d40f-102">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>
  <span data-ttu-id="4d40f-103">하나 이상의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 대해 최선의 구현 방법 정책에 대한 예약된 평가를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-103">You can configure scheduled evaluations of best practices policies on one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4d40f-104">일정에 따라 최선의 구현 방법 정책을 실행하도록 구성하려면 정책을 대상 인스턴스로 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-104">To configure best practices policies to run on a scheduled basis, you must import the policies into the target instance.</span></span>  
  
 <span data-ttu-id="4d40f-105">예약된 정책을 여러 서버에 배포하려면 정책을 하나의 인스턴스로 가져와 각 정책에 대한 일정을 구성하고 예약된 정책을 폴더로 내보낸 다음 등록된 서버를 통해 예약된 정책을 대상 인스턴스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-105">To deploy scheduled policies to multiple servers, you can import the policies to one instance, configure the schedules for each policy, export the scheduled policies to a folder, and then deploy the scheduled policies to target instances through Registered Servers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4d40f-106">대상 인스턴스는 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 이상 버전을 실행 중이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-106">The target instances must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="4d40f-107">자동화를 수행하려면 정책을 인스턴스에 로컬로 저장해야 합니다. 이 기능은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 이전 버전인 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]에서는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-107">Automation requires the policies to be stored locally on the instance, which is not supported by versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="4d40f-108">이 단원에서는 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-108">In this lesson, you will do the following:</span></span>  
  
-   <span data-ttu-id="4d40f-109">최선의 구현 방법 정책을 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]인스턴스로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-109">Import the best practices policies into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="4d40f-110">일정에 따라 정책을 실행하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-110">Configure the policies to run on a schedule.</span></span>  
  
-   <span data-ttu-id="4d40f-111">예약된 최선의 구현 방법 정책을 등록된 서버를 통해 여러 인스턴스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-111">Deploy the scheduled best practices policies to multiple instances through Registered Servers.</span></span>  
  
 <span data-ttu-id="4d40f-112">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="4d40f-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="4d40f-113">단일 인스턴스로 정책 가져오기</span><span class="sxs-lookup"><span data-stu-id="4d40f-113">Import the Policies to a Single Instance</span></span>](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [<span data-ttu-id="4d40f-114">정책 예약</span><span class="sxs-lookup"><span data-stu-id="4d40f-114">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
-   [<span data-ttu-id="4d40f-115">여러 인스턴스에 예약된 정책 배포</span><span class="sxs-lookup"><span data-stu-id="4d40f-115">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a><span data-ttu-id="4d40f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d40f-116">See Also</span></span>  
 [<span data-ttu-id="4d40f-117">중앙 관리 서버를 사용 하 여 여러 서버 관리</span><span class="sxs-lookup"><span data-stu-id="4d40f-117">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
