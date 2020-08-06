---
title: 스크립트 생성 마법사에 지원되는 개체
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ddc1da0d2f87fc12dfbe034a683802f54b7d34f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659928"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a><span data-ttu-id="83460-102">스크립트 생성 마법사에 지원되는 개체</span><span class="sxs-lookup"><span data-stu-id="83460-102">Objects Supported by the Generate Scripts Wizard</span></span>
  <span data-ttu-id="83460-103">스크립트 생성 및 게시 마법사는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서 지원되는 개체의 하위 집합을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="83460-103">The Generate and Publish Scripts wizard supports a subset of the objects supported by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="supported-objects"></a><span data-ttu-id="83460-104">지원되는 개체</span><span class="sxs-lookup"><span data-stu-id="83460-104">Supported Objects</span></span>  
 <span data-ttu-id="83460-105">다음 표에서는 스크립트 생성 및 게시 마법사가 지원하는 개체를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="83460-105">The following table lists the objects that can be published supported by the Generate and Publish Scripts Wizard.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="83460-106">애플리케이션 역할</span><span class="sxs-lookup"><span data-stu-id="83460-106">Application role</span></span>|<span data-ttu-id="83460-107">데이터베이스 역할</span><span class="sxs-lookup"><span data-stu-id="83460-107">Database role</span></span>|<span data-ttu-id="83460-108">스키마</span><span class="sxs-lookup"><span data-stu-id="83460-108">Schema</span></span>|<span data-ttu-id="83460-109">사용자 정의 집계</span><span class="sxs-lookup"><span data-stu-id="83460-109">User-defined aggregate</span></span>|<span data-ttu-id="83460-110">보기<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="83460-110">View<sup>1</sup></span></span>|  
|<span data-ttu-id="83460-111">어셈블리</span><span class="sxs-lookup"><span data-stu-id="83460-111">Assembly</span></span>|<span data-ttu-id="83460-112">DEFAULT 제약 조건</span><span class="sxs-lookup"><span data-stu-id="83460-112">DEFAULT constraint</span></span>|<span data-ttu-id="83460-113">저장 프로시저<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="83460-113">Stored procedure<sup>1</sup></span></span>|<span data-ttu-id="83460-114">사용자 정의 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="83460-114">User-defined data type</span></span>|<span data-ttu-id="83460-115">XML 스키마 컬렉션</span><span class="sxs-lookup"><span data-stu-id="83460-115">XML schema collection</span></span>|  
|<span data-ttu-id="83460-116">CHECK 제약 조건</span><span class="sxs-lookup"><span data-stu-id="83460-116">CHECK constraint</span></span>|<span data-ttu-id="83460-117">전체 텍스트 카탈로그</span><span class="sxs-lookup"><span data-stu-id="83460-117">Full-text catalog</span></span>|<span data-ttu-id="83460-118">동의어</span><span class="sxs-lookup"><span data-stu-id="83460-118">Synonym</span></span>|<span data-ttu-id="83460-119">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="83460-119">User-defined function</span></span>||  
|<span data-ttu-id="83460-120">CLR (공용 언어 런타임) 저장 프로시저<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="83460-120">CLR (common language runtime) stored procedure<sup>1</sup></span></span>|<span data-ttu-id="83460-121">인덱스</span><span class="sxs-lookup"><span data-stu-id="83460-121">Index</span></span>|<span data-ttu-id="83460-122">테이블</span><span class="sxs-lookup"><span data-stu-id="83460-122">Table</span></span>|<span data-ttu-id="83460-123">사용자 정의 테이블</span><span class="sxs-lookup"><span data-stu-id="83460-123">User-defined table</span></span>||  
|<span data-ttu-id="83460-124">CLR 사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="83460-124">CLR user-defined function</span></span>|<span data-ttu-id="83460-125">규칙</span><span class="sxs-lookup"><span data-stu-id="83460-125">Rule</span></span>|<span data-ttu-id="83460-126">사용자<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="83460-126">User<sup>2</sup></span></span>|<span data-ttu-id="83460-127">사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="83460-127">User-defined type</span></span>||  
  
 <span data-ttu-id="83460-128"><sup>1</sup> 암호화 하지 않고 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83460-128"><sup>1</sup> Published without encryption.</span></span>  
  
 <span data-ttu-id="83460-129"><sup>2</sup> 데이터베이스에 있는 시스템 사용자 이외의 모든 사용자는 역할로 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83460-129"><sup>2</sup> Any non-system users that exist in the database are published as Roles.</span></span>  
  
  
