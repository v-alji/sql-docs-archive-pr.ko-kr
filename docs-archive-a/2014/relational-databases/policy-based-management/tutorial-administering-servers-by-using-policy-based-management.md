---
title: '자습서: 정책 기반 관리를 사용하여 서버 관리 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Policy-Based Management]
- Policy-Based Management, tutorials
ms.assetid: 7de96e7b-9fb8-4cc8-8d85-61345d68a1e8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9b707a5ecd362c6b3b54e853f89d79e25a9e1428
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648991"
---
# <a name="tutorial-administering-servers-by-using-policy-based-management"></a><span data-ttu-id="faf45-102">자습서: 정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="faf45-102">Tutorial: Administering Servers by Using Policy-Based Management</span></span>
  <span data-ttu-id="faf45-103">정책 기반 관리 정책을 사용하여 서버 관리 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-103">Welcome to the Administering Servers by Using Policy-Based Management Policies tutorial.</span></span> <span data-ttu-id="faf45-104">이 자습서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에는 익숙하지만 정책 기반 관리에는 경험이 없는 사용자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-104">This tutorial is intended for users who are familiar with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] but new to the Policy-Based Management.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="faf45-105">학습 내용</span><span class="sxs-lookup"><span data-stu-id="faf45-105">What You Will Learn</span></span>  
 <span data-ttu-id="faf45-106">이 자습서에서는 서버를 관리하기 위한 정책과 단일 데이터베이스에 적용되는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-106">This tutorial creates a policy to administer your server and a policy that applies to a single database.</span></span> <span data-ttu-id="faf45-107">한 정책은 준수 여부 테스트를 위해 요청 시 실행되고</span><span class="sxs-lookup"><span data-stu-id="faf45-107">One policy is run on demand to test for compliance.</span></span> <span data-ttu-id="faf45-108">다른 정책은 앞으로 정책이 준수되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-108">The other policy enforces future compliance.</span></span>  
  
 <span data-ttu-id="faf45-109">이 자습서는 다음 두 단원으로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-109">This tutorial is divided into two lessons:</span></span>  
  
 [<span data-ttu-id="faf45-110">1단원: Off By Default 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="faf45-110">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
 <span data-ttu-id="faf45-111">이 단원에서는 서버에 데이터베이스 메일이 설정되지 않아야 함을 지정하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-111">This lesson creates a policy that specifies that Database Mail is not enabled on the server.</span></span> <span data-ttu-id="faf45-112">그런 다음 서버가 해당 정책을 준수하는지 확인하고 데이터베이스 메일을 해제하여 서버를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-112">Then, it checks to see whether your server complies with the policy, and configures the server by disabling Database Mail.</span></span>  
  
 [<span data-ttu-id="faf45-113">2단원: 명명 표준 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="faf45-113">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
 <span data-ttu-id="faf45-114">이 단원에서는 테이블 명명 표준을 정의하고 적용하는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-114">This lesson creates a policy that defines and enforces a naming standard for tables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faf45-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="faf45-115">Requirements</span></span>  
 <span data-ttu-id="faf45-116">이 단원을 진행하려면 데이터베이스 및 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 기본적으로 이해해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-116">This lesson requires basic database knowledge and a basic understanding of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="faf45-117">이 자습서를 사용하려면 시스템에 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faf45-117">To use this tutorial, your system must have [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] installed.</span></span>  
  
## <a name="start-the-tutorial"></a><span data-ttu-id="faf45-118">자습서 시작</span><span class="sxs-lookup"><span data-stu-id="faf45-118">Start the Tutorial</span></span>  
 [<span data-ttu-id="faf45-119">1단원: Off By Default 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="faf45-119">Lesson 1: Create and Apply an Off By Default Policy</span></span>](lesson-1-create-and-apply-an-off-by-default-policy.md)  
  
## <a name="see-also"></a><span data-ttu-id="faf45-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="faf45-120">See Also</span></span>  
 [<span data-ttu-id="faf45-121">정책 기반 관리를 사용하여 서버 관리</span><span class="sxs-lookup"><span data-stu-id="faf45-121">Administer Servers by Using Policy-Based Management</span></span>](administer-servers-by-using-policy-based-management.md)  
  
  
