---
title: MSSQL_ENG021330 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4338756a641b23bfc6f52da6b3de296bb6415756
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730503"
---
# <a name="mssql_eng021330"></a><span data-ttu-id="d65e4-102">MSSQL_ENG021330</span><span class="sxs-lookup"><span data-stu-id="d65e4-102">MSSQL_ENG021330</span></span>
    
## <a name="message-details"></a><span data-ttu-id="d65e4-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="d65e4-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d65e4-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d65e4-104">Product Name</span></span>|<span data-ttu-id="d65e4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d65e4-105">SQL Server</span></span>|  
|<span data-ttu-id="d65e4-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d65e4-106">Event ID</span></span>|<span data-ttu-id="d65e4-107">21330</span><span class="sxs-lookup"><span data-stu-id="d65e4-107">21330</span></span>|  
|<span data-ttu-id="d65e4-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d65e4-108">Event Source</span></span>|<span data-ttu-id="d65e4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d65e4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d65e4-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d65e4-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="d65e4-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d65e4-111">Symbolic Name</span></span>||  
|<span data-ttu-id="d65e4-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d65e4-112">Message Text</span></span>|<span data-ttu-id="d65e4-113">복제 작업 디렉터리(%ls)에 하위 디렉터리를 만들지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="d65e4-113">Failed to create a sub-directory under the replication working directory.(%ls)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d65e4-114">설명</span><span class="sxs-lookup"><span data-stu-id="d65e4-114">Explanation</span></span>  
 <span data-ttu-id="d65e4-115">이 오류는 구독을 수동으로 초기화하는 경우와 복제 스크립트가 저장되는 디렉터리를 만드는 데 문제가 생기는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d65e4-115">This error can occur when a subscription is initialized manually, and there is a problem creating the directory in which replication scripts are stored.</span></span> <span data-ttu-id="d65e4-116">이 오류는 권한 문제로 인해 발생할 수도 있습니다. 예를 들어 스냅샷을 사용하지 않고 구독을 초기화할 경우 게시자에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행하는 계정에는 배포자의 스냅샷 폴더에 대한 쓰기 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d65e4-116">The error can be caused by a permissions issue: when a subscription is initialized without using a snapshot, the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher must have write permissions on the snapshot folder at the Distributor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d65e4-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d65e4-117">User Action</span></span>  
 <span data-ttu-id="d65e4-118">스냅샷 폴더에 대해 올바른 경로가 지정되었는지 확인하고 게시자에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스를 실행하는 계정에 충분한 사용 권한이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d65e4-118">Ensure that the correct path has been specified for the snapshot folder and that the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher has sufficient permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d65e4-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d65e4-119">See Also</span></span>  
 <span data-ttu-id="d65e4-120">[기본 스냅숏 위치 지정](snapshot-options.md#snapshot-folder-locations) </span><span class="sxs-lookup"><span data-stu-id="d65e4-120">[Specify the Default Snapshot Location](snapshot-options.md#snapshot-folder-locations) </span></span>  
 <span data-ttu-id="d65e4-121">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="d65e4-121">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="d65e4-122">스냅샷 없이 트랜잭션 구독 초기화</span><span class="sxs-lookup"><span data-stu-id="d65e4-122">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
