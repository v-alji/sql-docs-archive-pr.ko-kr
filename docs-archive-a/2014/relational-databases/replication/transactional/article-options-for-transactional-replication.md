---
title: 트랜잭션 복제를 위한 아티클 옵션 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1cc13a3d11e35ed47eac4ff401fb8b7cb607b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651634"
---
# <a name="article-options-for-transactional-replication"></a><span data-ttu-id="74a07-102">트랜잭션 복제를 위한 아티클 옵션</span><span class="sxs-lookup"><span data-stu-id="74a07-102">Article Options for Transactional Replication</span></span>
  <span data-ttu-id="74a07-103">트랜잭션 게시의 아티클에는 여러 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-103">There are a number of options for articles in transactional publications.</span></span> <span data-ttu-id="74a07-104">트랜잭션 복제를 사용하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-104">With transactional replication, you can do the following:</span></span>  
  
-   <span data-ttu-id="74a07-105">게시자에서 구독자로 변경 내용이 전파되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-105">Specify how changes are propagated from the Publisher to Subscribers.</span></span> <span data-ttu-id="74a07-106">자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a07-106">For more information, see [Specify How Changes Are Propagated for Transactional Articles](transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
-   <span data-ttu-id="74a07-107">저장 프로시저의 실행 결과를 복제하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-107">Specify that the execution of a stored procedure be replicated.</span></span> <span data-ttu-id="74a07-108">이는 많은 데이터에 영향을 주는 유지 관리 관련 저장 프로시저의 결과를 복제할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-108">This is useful in replicating the results of maintenance-oriented stored procedures that affect large amounts of data.</span></span> <span data-ttu-id="74a07-109">자세한 내용은 [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a07-109">For more information, see [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).</span></span>  
  
-   <span data-ttu-id="74a07-110">제약 조건 및 트리거를 구독자로 복사할지 여부와 같은 스키마 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-110">Specify schema options, such as whether constraints and triggers are copied to the Subscriber.</span></span> <span data-ttu-id="74a07-111">자세한 내용은 [스키마 옵션 지정](../publish/specify-schema-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a07-111">For more information, see [Specify Schema Options](../publish/specify-schema-options.md).</span></span>  
  
-   <span data-ttu-id="74a07-112">행 필터와 열 필터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-112">Use row filters and column filters.</span></span> <span data-ttu-id="74a07-113">테이블 아티클을 필터링하여 게시할 데이터 파티션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a07-113">Filtering table articles enables you to create partitions of data to be published.</span></span> <span data-ttu-id="74a07-114">자세한 내용은 [게시된 데이터 필터링](../publish/filter-published-data.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="74a07-114">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a07-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="74a07-115">See Also</span></span>  
 [<span data-ttu-id="74a07-116">데이터 및 데이터베이스 개체 게시</span><span class="sxs-lookup"><span data-stu-id="74a07-116">Publish Data and Database Objects</span></span>](../publish/publish-data-and-database-objects.md)  
  
  
