---
title: MSSQLSERVER_5237 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653883"
---
# <a name="mssqlserver_5237"></a><span data-ttu-id="4e2a4-102">MSSQLSERVER_5237</span><span class="sxs-lookup"><span data-stu-id="4e2a4-102">MSSQLSERVER_5237</span></span>
    
## <a name="details"></a><span data-ttu-id="4e2a4-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="4e2a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4e2a4-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="4e2a4-104">Product Name</span></span>|<span data-ttu-id="4e2a4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="4e2a4-105">SQL Server</span></span>|  
|<span data-ttu-id="4e2a4-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="4e2a4-106">Event ID</span></span>|<span data-ttu-id="4e2a4-107">5237</span><span class="sxs-lookup"><span data-stu-id="4e2a4-107">5237</span></span>|  
|<span data-ttu-id="4e2a4-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="4e2a4-108">Event Source</span></span>|<span data-ttu-id="4e2a4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="4e2a4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="4e2a4-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="4e2a4-110">Component</span></span>|<span data-ttu-id="4e2a4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="4e2a4-111">SQLEngine</span></span>|  
|<span data-ttu-id="4e2a4-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="4e2a4-112">Symbolic Name</span></span>|<span data-ttu-id="4e2a4-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span><span class="sxs-lookup"><span data-stu-id="4e2a4-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span></span>|  
|<span data-ttu-id="4e2a4-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="4e2a4-114">Message Text</span></span>|<span data-ttu-id="4e2a4-115">내부 쿼리 오류로 인해 개체 'NAME'(개체 ID O_ID)에 대한 DBCC 크로스-행 집합 검사에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="4e2a4-115">DBCC cross-rowset check failed for object 'NAME' (object ID O_ID) due to an internal query error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4e2a4-116">설명</span><span class="sxs-lookup"><span data-stu-id="4e2a4-116">Explanation</span></span>  
 <span data-ttu-id="4e2a4-117">DBCC의 내부 오류로 인해 인덱싱된 뷰를 확인하는 쿼리를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e2a4-117">An internal error resulted in DBCC not being able to execute the query to check indexed views.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4e2a4-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="4e2a4-118">User Action</span></span>  
 <span data-ttu-id="4e2a4-119">DBCC 명령을 다시 실행하십시오.</span><span class="sxs-lookup"><span data-stu-id="4e2a4-119">Rerun the DBCC command.</span></span>  
  
  
