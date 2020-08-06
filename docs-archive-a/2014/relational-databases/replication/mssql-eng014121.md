---
title: MSSQL_ENG014121 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04d4cbdd2197745d2d795814d88c4f7bc28eb90e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638683"
---
# <a name="mssql_eng014121"></a><span data-ttu-id="a2e8d-102">MSSQL_ENG014121</span><span class="sxs-lookup"><span data-stu-id="a2e8d-102">MSSQL_ENG014121</span></span>
    
## <a name="message-details"></a><span data-ttu-id="a2e8d-103">메시지 정보</span><span class="sxs-lookup"><span data-stu-id="a2e8d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2e8d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="a2e8d-104">Product Name</span></span>|<span data-ttu-id="a2e8d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a2e8d-105">SQL Server</span></span>|  
|<span data-ttu-id="a2e8d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="a2e8d-106">Event ID</span></span>|<span data-ttu-id="a2e8d-107">14121</span><span class="sxs-lookup"><span data-stu-id="a2e8d-107">14121</span></span>|  
|<span data-ttu-id="a2e8d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="a2e8d-108">Event Source</span></span>|<span data-ttu-id="a2e8d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a2e8d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a2e8d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a2e8d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="a2e8d-111">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="a2e8d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="a2e8d-112">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="a2e8d-112">Message Text</span></span>|<span data-ttu-id="a2e8d-113">배포자 '%s'을(를) 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-113">Could not drop the Distributor '%s'.</span></span> <span data-ttu-id="a2e8d-114">이 배포자가 배포 데이터베이스와 연관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-114">This Distributor has associated distribution databases.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a2e8d-115">설명</span><span class="sxs-lookup"><span data-stu-id="a2e8d-115">Explanation</span></span>  
 <span data-ttu-id="a2e8d-116">배포자로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 연결된 배포 데이터베이스가 있으므로 해당 인스턴스를 배포자 역할에서 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-116">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance that is configured as a Distributor cannot be removed from the role of Distributor because there are distribution databases associated with the instance.</span></span> <span data-ttu-id="a2e8d-117">이 오류는 하나 이상의 게시자와 연결된 배포 데이터베이스를 삭제하려고 할 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-117">This error occurs if you attempt to drop a distribution database that is associated with one or more Publishers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a2e8d-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="a2e8d-118">User Action</span></span>  
 <span data-ttu-id="a2e8d-119">이 배포자와 연결된 게시자 및 배포 데이터베이스의 이름을 찾으려면 배포자의 데이터베이스에서 [sp_helpdistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-119">To find the names of any Publishers and distribution databases associated with this Distributor, execute [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql) from any database on the Distributor.</span></span>  
  
 <span data-ttu-id="a2e8d-120">이 배포자와 연결된 배포 데이터베이스에 대해 [sp_dropdistributiondb&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-120">Execute [sp_dropdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) for any distribution databases associated with this Distributor.</span></span> <span data-ttu-id="a2e8d-121">모든 배포 데이터베이스 연결을 제거한 다음 배포를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2e8d-121">After all distribution database associations are removed, you can disable distribution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e8d-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2e8d-122">See Also</span></span>  
 <span data-ttu-id="a2e8d-123">[오류 및 이벤트 참조&#40;복제&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="a2e8d-123">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="a2e8d-124">배포 구성</span><span class="sxs-lookup"><span data-stu-id="a2e8d-124">Configure Distribution</span></span>](configure-distribution.md)  
  
  
