---
title: MSSQLSERVER_12329 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7576e32946ce0a453637273c449bbff20e5b6fac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651041"
---
# <a name="mssqlserver_12329"></a><span data-ttu-id="5f012-102">MSSQLSERVER_12329</span><span class="sxs-lookup"><span data-stu-id="5f012-102">MSSQLSERVER_12329</span></span>
    
## <a name="details"></a><span data-ttu-id="5f012-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5f012-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f012-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5f012-104">Product Name</span></span>|<span data-ttu-id="5f012-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5f012-105">SQL Server</span></span>|  
|<span data-ttu-id="5f012-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5f012-106">Event ID</span></span>|<span data-ttu-id="5f012-107">12329</span><span class="sxs-lookup"><span data-stu-id="5f012-107">12329</span></span>|  
|<span data-ttu-id="5f012-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5f012-108">Event Source</span></span>|<span data-ttu-id="5f012-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5f012-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5f012-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5f012-110">Component</span></span>|<span data-ttu-id="5f012-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5f012-111">SQLEngine</span></span>|  
|<span data-ttu-id="5f012-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5f012-112">Symbolic Name</span></span>|<span data-ttu-id="5f012-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span><span class="sxs-lookup"><span data-stu-id="5f012-113">HK_UNSUPPORTED_NON_LATIN_CODEPAGE</span></span>|  
|<span data-ttu-id="5f012-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5f012-114">Message Text</span></span>|<span data-ttu-id="5f012-115">1252가 아닌 코드 페이지가 있는 데이터 정렬을 사용하는 데이터 형식 char(n) 및 varchar(n)는 *construct*에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f012-115">The data types char(n) and varchar(n) using a collation that has a code page other than 1252 are not supported with  *construct*.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f012-116">설명</span><span class="sxs-lookup"><span data-stu-id="5f012-116">Explanation</span></span>  
 <span data-ttu-id="5f012-117">1252가 아닌 코드 페이지가 있는 데이터 정렬을 사용하는 데이터 형식 char(n) 및 varchar(n)를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="5f012-117">Do not use the data types char(n) and varchar(n) using a collation that has a code page other than 1252.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f012-118">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5f012-118">User Action</span></span>  
 <span data-ttu-id="5f012-119">이 오류를 발생시킬 수 있는 예기치 않은 한 가지 상황은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5f012-119">One unexpected situation that can generate this error is:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 <span data-ttu-id="5f012-120">대신 다음을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="5f012-120">Use this instead:</span></span>  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
