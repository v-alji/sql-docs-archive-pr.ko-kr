---
title: 저장 프로시저의 쿼리 컨텍스트 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9da8ddb223ed03c0208fe524ea5cd7195a039c97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727436"
---
# <a name="accessing-query-context-in-stored-procedures"></a><span data-ttu-id="2f41a-102">저장 프로시저의 쿼리 컨텍스트 액세스</span><span class="sxs-lookup"><span data-stu-id="2f41a-102">Accessing Query Context in Stored Procedures</span></span>
  <span data-ttu-id="2f41a-103">저장 프로시저의 실행 컨텍스트는 ADOMD.NET 서버 개체 모델의 `Context` 개체로 저장 프로시저 코드 내에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-103">The execution context of a stored procedure is available within the code of the stored procedure as the `Context` object of the ADOMD.NET server object model.</span></span> <span data-ttu-id="2f41a-104">이것은 읽기 전용 컨텍스트이며 저장 프로시저로 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-104">This is a read-only context and cannot be modified by the stored procedure.</span></span> <span data-ttu-id="2f41a-105">이 개체에 다음 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-105">The following properties are available on this object.</span></span>  
  
|<span data-ttu-id="2f41a-106">속성</span><span class="sxs-lookup"><span data-stu-id="2f41a-106">Property</span></span>|<span data-ttu-id="2f41a-107">Type</span><span class="sxs-lookup"><span data-stu-id="2f41a-107">Type</span></span>|<span data-ttu-id="2f41a-108">Description</span><span class="sxs-lookup"><span data-stu-id="2f41a-108">Description</span></span>|  
|--------------|----------|-----------------|  
|<span data-ttu-id="2f41a-109">**CurrentCube**</span><span class="sxs-lookup"><span data-stu-id="2f41a-109">**CurrentCube**</span></span>|<span data-ttu-id="2f41a-110">큐브</span><span class="sxs-lookup"><span data-stu-id="2f41a-110">Cube</span></span>|<span data-ttu-id="2f41a-111">현재 쿼리 컨텍스트에 대한 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-111">The cube for the current query context.</span></span>|  
|<span data-ttu-id="2f41a-112">**CurrentDatabaseName**</span><span class="sxs-lookup"><span data-stu-id="2f41a-112">**CurrentDatabaseName**</span></span>|<span data-ttu-id="2f41a-113">String</span><span class="sxs-lookup"><span data-stu-id="2f41a-113">String</span></span>|<span data-ttu-id="2f41a-114">현재 데이터베이스의 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-114">The identifier of the current database.</span></span>|  
|<span data-ttu-id="2f41a-115">**CurrentConnection**</span><span class="sxs-lookup"><span data-stu-id="2f41a-115">**CurrentConnection**</span></span>|<span data-ttu-id="2f41a-116">연결</span><span class="sxs-lookup"><span data-stu-id="2f41a-116">Connection</span></span>|<span data-ttu-id="2f41a-117">현재 컨텍스트의 연결 개체에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-117">A reference to the connection object in the current context.</span></span>|  
|<span data-ttu-id="2f41a-118">**통과**</span><span class="sxs-lookup"><span data-stu-id="2f41a-118">**Pass**</span></span>|<span data-ttu-id="2f41a-119">정수</span><span class="sxs-lookup"><span data-stu-id="2f41a-119">Integer</span></span>|<span data-ttu-id="2f41a-120">현재 컨텍스트의 패스 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-120">The pass number for the current context.</span></span>|  
  
 <span data-ttu-id="2f41a-121">저장 프로시저에서 MDX(Multidimensional Expressions) 개체 모델을 사용할 경우 `Context` 개체가 존재하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-121">The `Context` object exists when the Multidimensional Expressions (MDX) object model is used in a stored procedure.</span></span> <span data-ttu-id="2f41a-122">그러나 클라이언트에서 MDX 개체 모델을 사용할 경우에는 이 개체를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-122">It is not available when the MDX object model is used on a client.</span></span> <span data-ttu-id="2f41a-123">`Context` 개체는 저장 프로시저에 명시적으로 전달되거나 저장 프로시저에서 명시적으로 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-123">The `Context` object is not explicitly passed to or returned by the stored procedure.</span></span> <span data-ttu-id="2f41a-124">이 개체는 저장 프로시저 실행 중에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f41a-124">It is available during the execution of the stored procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f41a-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f41a-125">See Also</span></span>  
 <span data-ttu-id="2f41a-126">[다차원 모델 어셈블리 관리](../multidimensional-models/multidimensional-model-assemblies-management.md) </span><span class="sxs-lookup"><span data-stu-id="2f41a-126">[Multidimensional Model Assemblies Management](../multidimensional-models/multidimensional-model-assemblies-management.md) </span></span>  
 [<span data-ttu-id="2f41a-127">저장 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="2f41a-127">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
