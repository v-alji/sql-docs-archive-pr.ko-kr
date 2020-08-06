---
title: 복제 자습서 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- walkthroughs [SQL Server replication]
- replication [SQL Server], tutorials
ms.assetid: 19fbd10e-5b59-4cd0-a988-52d5d9206242
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f4d70abd6c58b3eb0fa4a53e2806ab1b3fbe9245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646317"
---
# <a name="replication-tutorials"></a><span data-ttu-id="25bc0-102">복제 자습서</span><span class="sxs-lookup"><span data-stu-id="25bc0-102">Replication Tutorials</span></span>
  <span data-ttu-id="25bc0-103">복제에는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 복제 토폴로지를 설정 및 실행하는 방법을 배우는 데 사용할 수 있는 자습서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-103">Replication includes tutorials that you can use to learn how to set up and run replication topologies using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="25bc0-104">복제 자습서에서 "게시자"는 복제되고 있는 원본 데이터가 있는 서버를 가리키며 "구독자"는 대상 서버를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-104">In the replication tutorials, "Publisher" refers to the server that contains that source data being replicated and "Subscriber" refers to the destination server.</span></span> <span data-ttu-id="25bc0-105">게시자와 구독자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 같은 인스턴스를 공유할 수 있지만 반드시 이렇게 해야 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-105">The Publisher and Subscriber may share the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], but it is not a requirement.</span></span> <span data-ttu-id="25bc0-106">자세한 내용은 [복제 게시 모델 개요](publish/replication-publishing-model-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25bc0-106">For more information, see [Replication Publishing Model Overview](publish/replication-publishing-model-overview.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="25bc0-107">이 자습서에 표시된 대부분의 태스크는 프로그래밍 방식으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-107">Most of the tasks shown in these tutorials can be performed programmatically.</span></span> <span data-ttu-id="25bc0-108">자세한 내용은 [개발자 가이드 &#40;Replication&#41;](concepts/replication-developer-documentation.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="25bc0-108">For more information, see [Developer's Guide &#40;Replication&#41;](concepts/replication-developer-documentation.md).</span></span>  
  
## <a name="replication-tutorials"></a><span data-ttu-id="25bc0-109">복제 자습서</span><span class="sxs-lookup"><span data-stu-id="25bc0-109">Replication Tutorials</span></span>  
 [<span data-ttu-id="25bc0-110">복제용 서버 준비</span><span class="sxs-lookup"><span data-stu-id="25bc0-110">Preparing the Server for Replication</span></span>](tutorial-preparing-the-server-for-replication.md)  
 <span data-ttu-id="25bc0-111">최소의 권한을 사용하여 복제를 실행할 수 있도록 서버를 준비하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-111">Learn how to prepare servers so that replication can be run with least privileges.</span></span> <span data-ttu-id="25bc0-112">다른 복제 자습서로 넘어가기 전에 이 자습서를 마쳐야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-112">You must complete this tutorial before the other replication tutorials.</span></span>  
  
 [<span data-ttu-id="25bc0-113">계속 연결된 서버 간 데이터 복제</span><span class="sxs-lookup"><span data-stu-id="25bc0-113">Replicating Data Between Continuously Connected Servers</span></span>](tutorial-replicating-data-between-continuously-connected-servers.md)  
 <span data-ttu-id="25bc0-114">트랜잭션 복제를 사용하여 완전히 연결된 서버 간에 데이터를 복제하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-114">Learn how to use transactional replication to replicate data between fully connected servers.</span></span>  
  
 [<span data-ttu-id="25bc0-115">모바일 클라이언트와의 데이터 복제</span><span class="sxs-lookup"><span data-stu-id="25bc0-115">Replicating Data with Mobile Clients</span></span>](tutorial-replicating-data-with-mobile-clients.md)  
 <span data-ttu-id="25bc0-116">병합 복제를 사용하여 한 서버와 가끔만 연결되는 하나 이상의 클라이언트 간에 데이터를 교환하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="25bc0-116">Learn how to use merge replication to exchange data between a server and one or more clients that are only occasionally connected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bc0-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25bc0-117">See Also</span></span>  
 [<span data-ttu-id="25bc0-118">SQL Server 복제 보안</span><span class="sxs-lookup"><span data-stu-id="25bc0-118">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  
