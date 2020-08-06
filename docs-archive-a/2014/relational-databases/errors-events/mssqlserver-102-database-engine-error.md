---
title: MSSQLSERVER_102 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 102 (Database Engine error)
ms.assetid: 264dc1a2-c8a0-4c89-b5f6-951baf950299
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 18c330b8d6a534ca11e2ad2c03f89793f8c832e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646540"
---
# <a name="mssqlserver_102"></a><span data-ttu-id="1d152-102">MSSQLSERVER_102</span><span class="sxs-lookup"><span data-stu-id="1d152-102">MSSQLSERVER_102</span></span>
    
## <a name="details"></a><span data-ttu-id="1d152-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="1d152-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d152-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="1d152-104">Product Name</span></span>|<span data-ttu-id="1d152-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1d152-105">SQL Server</span></span>|  
|<span data-ttu-id="1d152-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="1d152-106">Event ID</span></span>|<span data-ttu-id="1d152-107">102</span><span class="sxs-lookup"><span data-stu-id="1d152-107">102</span></span>|  
|<span data-ttu-id="1d152-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="1d152-108">Event Source</span></span>|<span data-ttu-id="1d152-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1d152-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1d152-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1d152-110">Component</span></span>|<span data-ttu-id="1d152-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1d152-111">SQLEngine</span></span>|  
|<span data-ttu-id="1d152-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="1d152-112">Symbolic Name</span></span>|<span data-ttu-id="1d152-113">P_SYNTAXERR2</span><span class="sxs-lookup"><span data-stu-id="1d152-113">P_SYNTAXERR2</span></span>|  
|<span data-ttu-id="1d152-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="1d152-114">Message Text</span></span>|<span data-ttu-id="1d152-115">'%.\*ls' 근처의 구문이 잘못되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-115">Incorrect syntax near '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d152-116">설명</span><span class="sxs-lookup"><span data-stu-id="1d152-116">Explanation</span></span>  
 <span data-ttu-id="1d152-117">구문 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-117">Indicates a syntax error.</span></span> <span data-ttu-id="1d152-118">오류로 인해 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 문을 처리할 수 없기 때문에 추가 정보를 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-118">Additional information is not available because the error prevents the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from processing the statement.</span></span>  
  
 <span data-ttu-id="1d152-119">이 오류는 90 또는 100 호환성 모드가 아닐 경우 사용되지 않는 RC4 또는 RC4_128 암호화를 사용하여 대칭 키를 만들려고 할 때 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-119">Can be caused by attempting to create a symmetric key using the deprecated RC4 or RC4_128 encryption, when not in 90 or 100 compatibility mode.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d152-120">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="1d152-120">User Action</span></span>  
 <span data-ttu-id="1d152-121">[!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 구문 오류를 검색하십시오.</span><span class="sxs-lookup"><span data-stu-id="1d152-121">Search the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement for syntax errors.</span></span>  
  
 <span data-ttu-id="1d152-122">RC4 또는 RC4_128을 사용하여 대칭 키를 만들 경우 AES 알고리즘 같은 최신 암호화 기술을 선택하는 것이</span><span class="sxs-lookup"><span data-stu-id="1d152-122">If creating a symmetric key using the RC4 or RC4_128, select a newer encryption such as one of the AES algorithms.</span></span> <span data-ttu-id="1d152-123">좋습니다. RC4를 꼭 사용해야 할 경우에는 ALTER DATABASE SET COMPATIBILITY_LEVEL을 사용하여 데이터베이스 호환성 수준을 90 또는 100으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-123">(Recommended.) If you must use RC4, use ALTER DATABASE SET COMPATIBILITY_LEVEL to set the database to compatibility level 90 or 100.</span></span> <span data-ttu-id="1d152-124">이 옵션은 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1d152-124">(Not recommended.)</span></span>  
  
  
