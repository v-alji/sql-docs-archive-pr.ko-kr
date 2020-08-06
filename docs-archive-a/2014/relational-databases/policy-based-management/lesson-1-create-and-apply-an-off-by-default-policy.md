---
title: '1단원: Off By Default 정책 만들기 및 적용 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: d31367db-b7db-44c4-8df2-f1240474cf78
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a76df1a72b93d09c5c1c199cb0246dbb51c9cbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646963"
---
# <a name="lesson-1-create-and-apply-an-off-by-default-policy"></a><span data-ttu-id="d01d7-102">1단원: Off By Default 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="d01d7-102">Lesson 1: Create and Apply an Off By Default Policy</span></span>
  <span data-ttu-id="d01d7-103">정책 기반 관리 정책을 사용하면 하나 이상의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 하나 이상의 인스턴스 개체, 서버 인스턴스, 하나 이상의 데이터베이스 또는 하나 이상의 데이터베이스 개체를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-103">Using Policy-Based Management policies, you can administer one or more instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], one or more instance objects, server instances, one or more databases, or one or more database objects.</span></span> <span data-ttu-id="d01d7-104">데이터베이스 관리자로서 특정 서버에 데이터베이스 메일이 설정되지 않도록 해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-104">As the database administrator, you want to ensure that certain servers do not have Database Mail enabled.</span></span> <span data-ttu-id="d01d7-105">이 단원에서는 해당 서버 옵션을 설정하는 조건과 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-105">In this lesson, you will create a condition and a policy that sets that server option.</span></span> <span data-ttu-id="d01d7-106">서버가 정책을 준수하는지 여부를 확인하기 위해 해당 서버를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-106">You will test the server to see whether it complies with the policy.</span></span> <span data-ttu-id="d01d7-107">그런 다음 해당 정책을 통해 서버를 다시 구성하여 서버가 정책을 준수하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-107">Then, you will use the policy to reconfigure the server to bring the server into compliance.</span></span>  
  
 <span data-ttu-id="d01d7-108">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="d01d7-108">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="d01d7-109">Off By Default 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="d01d7-109">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
-   [<span data-ttu-id="d01d7-110">Off By Default 정책을 실행하도록 서버 구성</span><span class="sxs-lookup"><span data-stu-id="d01d7-110">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="d01d7-111">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="d01d7-111">Next Task in Lesson</span></span>  
 [<span data-ttu-id="d01d7-112">Off By Default 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="d01d7-112">Create the Off By Default Policy</span></span>](lesson-1-1-create-the-off-by-default-policy.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="d01d7-113">다음 단원</span><span class="sxs-lookup"><span data-stu-id="d01d7-113">Next Lesson</span></span>  
 [<span data-ttu-id="d01d7-114">2단원: 명명 표준 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="d01d7-114">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
