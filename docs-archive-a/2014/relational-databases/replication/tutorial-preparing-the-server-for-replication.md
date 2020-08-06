---
title: '자습서: 복제용 서버 준비 | Microsoft 문서'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1f036ff2a111ee6b5f97655b9bebaf34391a436
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660998"
---
# <a name="tutorial-preparing-the-server-for-replication"></a><span data-ttu-id="e1599-102">자습서: 복제용 서버 준비</span><span class="sxs-lookup"><span data-stu-id="e1599-102">Tutorial: Preparing the Server for Replication</span></span>
  <span data-ttu-id="e1599-103">복제 토폴로지를 구성하려면 보안을 계획해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-103">It is important to plan for security before you configure your replication topology.</span></span> <span data-ttu-id="e1599-104">이 자습서에서는 데이터 복제의 첫 단계인 배포를 구성하는 방법과 복제 토폴로지의 보안을 강화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-104">This tutorial shows you how to better secure a replication topology as well as how to configure distribution, which is the first step in replicating data.</span></span> <span data-ttu-id="e1599-105">다른 자습서를 사용하기 전에 먼저 이 자습서를 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-105">You must complete this tutorial before any of the others.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e1599-106">서버 간 데이터를 안전하게 복제하려면 [복제 보안을 위한 최선의 구현 방법](security/replication-security-best-practices.md)의 모든 권장 사항을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-106">To replicate data securely between servers, you should implement all of the recommendations in [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="e1599-107">학습 내용</span><span class="sxs-lookup"><span data-stu-id="e1599-107">What You Will Learn</span></span>  
 <span data-ttu-id="e1599-108">이 자습서에서는 최소의 권한을 사용하여 안전하게 복제를 실행할 수 있도록 서버를 준비하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-108">In this tutorial you will learn how to prepare a server so that replication can run securely with least privileges.</span></span> <span data-ttu-id="e1599-109">첫 번째 단원에서는 복제 에이전트를 실행하는 데 사용되는 Windows 서비스 계정을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-109">The first lesson shows how to create the Windows service accounts used to run replication agents.</span></span> <span data-ttu-id="e1599-110">두 번째 단원에서는 게시 스냅샷을 생성하고 저장하는 데 사용되는 폴더를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-110">The second lesson shows how to configure the folder used to generate and store publication snapshots.</span></span> <span data-ttu-id="e1599-111">세 번째 단원에서는 배포를 구성하고 사용 권한을 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-111">The third lesson shows how to configure distribution and set permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1599-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e1599-112">Requirements</span></span>  
 <span data-ttu-id="e1599-113">이 자습서는 기본적인 데이터베이스 작업에는 익숙하지만 복제에 대한 경험은 풍부하지 않은 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-113">This tutorial is intended for users familiar with fundamental database operations, but who have limited exposure to replication.</span></span>  
  
 <span data-ttu-id="e1599-114">이 자습서를 사용하려면 시스템에 다음 구성 요소가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-114">To use this tutorial, your system must have the following components installed:</span></span>  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] <span data-ttu-id="e1599-115">데이터베이스가 있는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e1599-115">with the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="e1599-116">보안을 위해 예제 데이터베이스는 기본적으로 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1599-116">To enhance security, the sample databases are not installed by default.</span></span>  
  
 <span data-ttu-id="e1599-117">**이 자습서를 완료 하는 데 소요 되는 예상 시간: 30 분**</span><span class="sxs-lookup"><span data-stu-id="e1599-117">**Estimated time to complete this tutorial: 30 minutes.**</span></span>  
  
## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="e1599-118">이 자습서의 단원</span><span class="sxs-lookup"><span data-stu-id="e1599-118">Lessons in This Tutorial</span></span>  
  
-   [<span data-ttu-id="e1599-119">1단원: 복제용 Windows 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="e1599-119">Lesson 1: Creating Windows Accounts for Replication</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
-   [<span data-ttu-id="e1599-120">2단원: 스냅샷 폴더 준비</span><span class="sxs-lookup"><span data-stu-id="e1599-120">Lesson 2: Preparing the Snapshot Folder</span></span>](lesson-2-preparing-the-snapshot-folder.md)  
  
-   [<span data-ttu-id="e1599-121">3단원: 배포 구성</span><span class="sxs-lookup"><span data-stu-id="e1599-121">Lesson 3: Configuring Distribution</span></span>](lesson-3-configuring-distribution.md)  
  
 [<span data-ttu-id="e1599-122">자습서 시작</span><span class="sxs-lookup"><span data-stu-id="e1599-122">Start the Tutorial</span></span>](lesson-1-creating-windows-accounts-for-replication.md)  
  
## <a name="see-also"></a><span data-ttu-id="e1599-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1599-123">See Also</span></span>  
 <span data-ttu-id="e1599-124">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="e1599-124">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="e1599-125">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="e1599-125">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
