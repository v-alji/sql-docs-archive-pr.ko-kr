---
title: MSSQLSERVER_1793 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731668"
---
# <a name="mssqlserver_1793"></a><span data-ttu-id="6a1cd-102">MSSQLSERVER_1793</span><span class="sxs-lookup"><span data-stu-id="6a1cd-102">MSSQLSERVER_1793</span></span>
    
## <a name="details"></a><span data-ttu-id="6a1cd-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="6a1cd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a1cd-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="6a1cd-104">Product Name</span></span>|<span data-ttu-id="6a1cd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6a1cd-105">SQL Server</span></span>|  
|<span data-ttu-id="6a1cd-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="6a1cd-106">Event ID</span></span>|<span data-ttu-id="6a1cd-107">1793</span><span class="sxs-lookup"><span data-stu-id="6a1cd-107">1793</span></span>|  
|<span data-ttu-id="6a1cd-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="6a1cd-108">Event Source</span></span>|<span data-ttu-id="6a1cd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6a1cd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6a1cd-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6a1cd-110">Component</span></span>|<span data-ttu-id="6a1cd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6a1cd-111">SQLEngine</span></span>|  
|<span data-ttu-id="6a1cd-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="6a1cd-112">Symbolic Name</span></span>|<span data-ttu-id="6a1cd-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span><span class="sxs-lookup"><span data-stu-id="6a1cd-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span></span>|  
|<span data-ttu-id="6a1cd-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="6a1cd-114">Message Text</span></span>|<span data-ttu-id="6a1cd-115">FILESTREAM 데이터에 지정된 파티션 구성표가 없으므로 '%.\*ls' 인덱스를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-115">Cannot drop index '%.\*ls' since a partition scheme is not specified for FILESTREAM data.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6a1cd-116">설명</span><span class="sxs-lookup"><span data-stu-id="6a1cd-116">Explanation</span></span>  
 <span data-ttu-id="6a1cd-117">이 메시지는 FILESTREAM 데이터가 들어 있는 테이블에서 클러스터형 인덱스를 삭제하려고 시도하고 기본 데이터에 대한 **MOVE TO** 절을 지정하지만 FILESTREAM 데이터에 대한 **FILESTREAM_ON** 절은 지정하지 않는 경우에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-117">This message occurs when you try to drop a clustered index on a table that contains FILESTREAM data, and you specify a **MOVE TO** clause for the base data, but you do not specify a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6a1cd-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="6a1cd-118">User Action</span></span>  
 <span data-ttu-id="6a1cd-119">FILESTREAM 데이터가 들어 있는 테이블에서 클러스터형 인덱스를 삭제하는 경우 다음 옵션 중 하나를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-119">When dropping a clustered index on a table that contains FILESTREAM data, use one of the following options:</span></span>  
  
-   <span data-ttu-id="6a1cd-120">기본 데이터에 대한 **MOVE TO** 절과 FILESTREAM 데이터에 대한 **FILESTREAM_ON** 절을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-120">Specify both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
-   <span data-ttu-id="6a1cd-121">기본 데이터에 대한 **MOVE TO** 절이나 FILESTREAM 데이터에 대한 **FILESTREAM_ON** 절을 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-121">Do not specify either a **MOVE TO** clause for the base data or a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
 <span data-ttu-id="6a1cd-122">다음 예는 파티션 구성표가 기본 데이터에 대해서는 지정되어 있지만 FILESTREAM 데이터에 대해서는 지정되어 있지 않기 때문에 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-122">The following example fails because a partition scheme is specified for the base data, but is not specified for the FILESTREAM data.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 <span data-ttu-id="6a1cd-123">다음 예제는 기본 데이터에 대한 **MOVE TO** 절과 FILESTREAM 데이터에 대한 **FILESTREAM_ON** 절이 모두 지정되어 있기 때문에 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-123">The following example succeeds because both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data are specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 <span data-ttu-id="6a1cd-124">또한 다음 예제는 기본 데이터에 대한 **MOVE TO** 절이나 FILESTREAM 데이터에 대한 **FILESTREAM_ON** 절이 둘 다 지정되어 있지 않기 때문에 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="6a1cd-124">The following example also succeeds because neither a **MOVE TO** clause for the base data nor a **FILESTREAM_ON** clause for the FILESTREAM data is specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
