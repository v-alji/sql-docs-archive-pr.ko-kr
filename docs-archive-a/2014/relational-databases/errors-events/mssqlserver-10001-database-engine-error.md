---
title: MSSQLSERVER_10001 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10001 (Database Engine error)
ms.assetid: f8fd2d8d-a4af-4b6a-ba51-9123b7e4c9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0542f6d52a4fd194c4b0ae5d1aad501f5e3b8c2d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735284"
---
# <a name="mssqlserver_10001"></a><span data-ttu-id="8fc4f-102">MSSQLSERVER_10001</span><span class="sxs-lookup"><span data-stu-id="8fc4f-102">MSSQLSERVER_10001</span></span>
    
## <a name="details"></a><span data-ttu-id="8fc4f-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="8fc4f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fc4f-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="8fc4f-104">Product Name</span></span>|<span data-ttu-id="8fc4f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8fc4f-105">SQL Server</span></span>|  
|<span data-ttu-id="8fc4f-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="8fc4f-106">Event ID</span></span>|<span data-ttu-id="8fc4f-107">10001</span><span class="sxs-lookup"><span data-stu-id="8fc4f-107">10001</span></span>|  
|<span data-ttu-id="8fc4f-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="8fc4f-108">Event Source</span></span>|<span data-ttu-id="8fc4f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8fc4f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8fc4f-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8fc4f-110">Component</span></span>|<span data-ttu-id="8fc4f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8fc4f-111">SQLEngine</span></span>|  
|<span data-ttu-id="8fc4f-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="8fc4f-112">Symbolic Name</span></span>|<span data-ttu-id="8fc4f-113">HR_E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="8fc4f-113">HR_E_UNEXPECTED</span></span>|  
|<span data-ttu-id="8fc4f-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="8fc4f-114">Message Text</span></span>|<span data-ttu-id="8fc4f-115">공급자에서 예기치 않은 치명적인 오류가 보고되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc4f-115">The provider reported an unexpected catastrophic failure.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8fc4f-116">설명</span><span class="sxs-lookup"><span data-stu-id="8fc4f-116">Explanation</span></span>  
 <span data-ttu-id="8fc4f-117">OLE DB 공급자를 호출하는 동안 분산 쿼리 처리에서 일반 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="8fc4f-117">Distributed query processing encountered a generic error while calling into the OLE DB provider.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8fc4f-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="8fc4f-118">User Action</span></span>  
 <span data-ttu-id="8fc4f-119">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 OLE DB 추적 이벤트를 수집하고 이 데이터를 OLE DB 공급자에 대한 제품 지원에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8fc4f-119">Collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and  provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc4f-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8fc4f-120">See Also</span></span>  
 <span data-ttu-id="8fc4f-121">[SQL Server Profiler 템플릿 및 권한](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="8fc4f-121">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="8fc4f-122">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="8fc4f-122">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
