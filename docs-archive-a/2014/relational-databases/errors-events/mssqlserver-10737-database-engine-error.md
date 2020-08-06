---
title: MSSQLSERVER_10737 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df8a4de014552d3aca00b3eb244f7ff8df56756b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653438"
---
# <a name="mssqlserver_10737"></a><span data-ttu-id="7dda3-102">MSSQLSERVER_10737</span><span class="sxs-lookup"><span data-stu-id="7dda3-102">MSSQLSERVER_10737</span></span>
    
## <a name="details"></a><span data-ttu-id="7dda3-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="7dda3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7dda3-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="7dda3-104">Product Name</span></span>|<span data-ttu-id="7dda3-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7dda3-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7dda3-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="7dda3-106">Event ID</span></span>|<span data-ttu-id="7dda3-107">10737</span><span class="sxs-lookup"><span data-stu-id="7dda3-107">10737</span></span>|  
|<span data-ttu-id="7dda3-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="7dda3-108">Event Source</span></span>|<span data-ttu-id="7dda3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="7dda3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="7dda3-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="7dda3-110">Component</span></span>|<span data-ttu-id="7dda3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="7dda3-111">SQLEngine</span></span>|  
|<span data-ttu-id="7dda3-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="7dda3-112">Symbolic Name</span></span>|<span data-ttu-id="7dda3-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span><span class="sxs-lookup"><span data-stu-id="7dda3-113">REBUILD_PARTITION_ALL_NOT_SPECIFIED</span></span>|  
|<span data-ttu-id="7dda3-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="7dda3-114">Message Text</span></span>|<span data-ttu-id="7dda3-115">ALTER TABLE REBUILD 또는 ALTER INDEX REBUILD 문에서 DATA_COMPRESSION 절에 지정된 파티션이 있으면 PARTITION=ALL을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dda3-115">In an ALTER TABLE REBUILD or ALTER INDEX REBUILD statement, when a partition is specified in a DATA_COMPRESSION clause, PARTITION=ALL must be specified.</span></span> <span data-ttu-id="7dda3-116">PARTITION=ALL 절은 DATA_COMPRESSION 절에 하위 집합만 지정된 경우에도 테이블 또는 인덱스의 모든 파티션이 다시 작성되도록 지원하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dda3-116">The PARTITION=ALL clause is used to reinforce that all partitions of the table or index will be rebuilt, even if only a subset is specified in the DATA_COMPRESSION clause.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="7dda3-117">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="7dda3-117">User Action</span></span>  
 <span data-ttu-id="7dda3-118">ALTER TABLE 또는 ALTER INDEX 문에 PARTITION=ALL 절을 추가하거나</span><span class="sxs-lookup"><span data-stu-id="7dda3-118">Add the PARTITION=ALL clause to the ALTER TABLE or ALTER INDEX statement.</span></span> <span data-ttu-id="7dda3-119">REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF})를 사용하여 특정 파티션을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="7dda3-119">Or, to rebuild a specific partition, use REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}).</span></span>  
  
  
