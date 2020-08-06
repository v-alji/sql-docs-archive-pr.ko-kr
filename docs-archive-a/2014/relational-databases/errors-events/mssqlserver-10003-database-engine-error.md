---
title: MSSQLSERVER_10003 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ea44fc9591602bfc8279924e10a1803d0d5a87a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646541"
---
# <a name="mssqlserver_10003"></a><span data-ttu-id="23617-102">MSSQLSERVER_10003</span><span class="sxs-lookup"><span data-stu-id="23617-102">MSSQLSERVER_10003</span></span>
    
## <a name="details"></a><span data-ttu-id="23617-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="23617-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23617-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="23617-104">Product Name</span></span>|<span data-ttu-id="23617-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="23617-105">SQL Server</span></span>|  
|<span data-ttu-id="23617-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="23617-106">Event ID</span></span>|<span data-ttu-id="23617-107">10003</span><span class="sxs-lookup"><span data-stu-id="23617-107">10003</span></span>|  
|<span data-ttu-id="23617-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="23617-108">Event Source</span></span>|<span data-ttu-id="23617-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="23617-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="23617-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="23617-110">Component</span></span>|<span data-ttu-id="23617-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="23617-111">SQLEngine</span></span>|  
|<span data-ttu-id="23617-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="23617-112">Symbolic Name</span></span>|<span data-ttu-id="23617-113">HR_E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="23617-113">HR_E_OUTOFMEMORY</span></span>|  
|<span data-ttu-id="23617-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="23617-114">Message Text</span></span>|<span data-ttu-id="23617-115">공급자의 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="23617-115">The provider ran out of memory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="23617-116">설명</span><span class="sxs-lookup"><span data-stu-id="23617-116">Explanation</span></span>  
 <span data-ttu-id="23617-117">부족한 시스템 메모리 때문에 OLE DB 공급자의 메모리가 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="23617-117">Low system memory has caused the OLE DB provider to run out of memory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="23617-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="23617-118">User Action</span></span>  
 <span data-ttu-id="23617-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="23617-119">Restart the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="23617-120">그래도 도움이 되지 않으면 컴퓨터를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="23617-120">If that does not help, restart the computer.</span></span> <span data-ttu-id="23617-121">문제가 지속되면 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 OLE DB 추적 이벤트를 수집하고 이 데이터를 OLE DB 공급자에 대한 제품 지원에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="23617-121">If the problem persists, collect OLE DB trace events using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] and provide this data to product support for the OLE DB provider.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23617-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="23617-122">See Also</span></span>  
 <span data-ttu-id="23617-123">[SQL Server Profiler 템플릿 및 권한](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="23617-123">[SQL Server Profiler Templates and Permissions](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md) </span></span>  
 [<span data-ttu-id="23617-124">SQL Server Native Client&#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="23617-124">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
