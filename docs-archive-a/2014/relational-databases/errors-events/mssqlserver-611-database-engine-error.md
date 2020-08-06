---
title: MSSQLSERVER_611 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f0caa1c218e8b80059c0c97aac652da7db870af3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660618"
---
# <a name="mssqlserver_611"></a><span data-ttu-id="69aa5-102">MSSQLSERVER_611</span><span class="sxs-lookup"><span data-stu-id="69aa5-102">MSSQLSERVER_611</span></span>
    
## <a name="details"></a><span data-ttu-id="69aa5-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="69aa5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69aa5-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="69aa5-104">Product Name</span></span>|<span data-ttu-id="69aa5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="69aa5-105">SQL Server</span></span>|  
|<span data-ttu-id="69aa5-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="69aa5-106">Event ID</span></span>|<span data-ttu-id="69aa5-107">611</span><span class="sxs-lookup"><span data-stu-id="69aa5-107">611</span></span>|  
|<span data-ttu-id="69aa5-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="69aa5-108">Event Source</span></span>|<span data-ttu-id="69aa5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="69aa5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="69aa5-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="69aa5-110">Component</span></span>|<span data-ttu-id="69aa5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="69aa5-111">SQLEngine</span></span>|  
|<span data-ttu-id="69aa5-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="69aa5-112">Symbolic Name</span></span>|<span data-ttu-id="69aa5-113">VAR_SIZE_TOO_BIG</span><span class="sxs-lookup"><span data-stu-id="69aa5-113">VAR_SIZE_TOO_BIG</span></span>|  
|<span data-ttu-id="69aa5-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="69aa5-114">Message Text</span></span>|<span data-ttu-id="69aa5-115">오버헤드를 포함한 전체 변수 열 크기가 한도보다 큰 %d바이트이기 때문에 행을 삽입하거나 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69aa5-115">Cannot insert or update a row because total variable column size, including overhead, is %d bytes more than the limit.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="69aa5-116">설명</span><span class="sxs-lookup"><span data-stu-id="69aa5-116">Explanation</span></span>  
 <span data-ttu-id="69aa5-117">최대 변수 열 크기가 스키마에서 허용하는 것보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="69aa5-117">The maximum variable column size is more than that allowed by the schema.</span></span> <span data-ttu-id="69aa5-118">VarDecimal 스토리지 형식을 사용할 때 변수 열 크기가 한도를 초과하거나, 변수 열 크기가 압축된 데이터 레코드에 대해 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 허용하는 한도를 초과하면 오류 611이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="69aa5-118">Error 611 is returned when the variable column is over the limit in the fixed case when vardecimal storage format is enabled, or when the variable column size is over the limit allowed in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for a compressed data record.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="69aa5-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="69aa5-119">User Action</span></span>  
 <span data-ttu-id="69aa5-120">레코드의 크기를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="69aa5-120">Reduce the size of the record.</span></span>  
  
  
