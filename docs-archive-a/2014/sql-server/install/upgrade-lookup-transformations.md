---
title: 조회 변환 업그레이드 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Lookup transformation and upgrading
- upgrading caching for Lookup transformation
- upgrading Lookup transformation
ms.assetid: d9b2c281-91ee-4e20-bdf0-0cd77d4a4241
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 74430ab1bed232b8d510a8c28a8a690d88d1f6ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646811"
---
# <a name="upgrade-lookup-transformations"></a><span data-ttu-id="48485-102">조회 변환 업그레이드</span><span class="sxs-lookup"><span data-stu-id="48485-102">Upgrade Lookup Transformations</span></span>
  <span data-ttu-id="48485-103">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 에서 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 로 업그레이드하는 경우 새로운 조회 변환 기능을 활용하도록 패키지를 수정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-103">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] consider modifying packages to take advantage of the new features in the Lookup Transformation.</span></span> <span data-ttu-id="48485-104">새로운 조회 변환에서는 [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]에서 사용할 수 있는 캐싱 유형 및 데이터 출력 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="48485-104">The transformation supports the caching types and data output options available in [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)].</span></span> <span data-ttu-id="48485-105">캐싱 및 데이터 출력에 대한 자세한 내용은 [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="48485-105">For more information about additional the caching and data outputs, see [Lookup Transformation](../../integration-services/data-flow/transformations/lookup-transformation.md).</span></span>  
  
 <span data-ttu-id="48485-106">[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]에서 사용할 수 있는 캐싱 유형으로는 전체 캐싱, 부분 캐싱 및 캐싱 안 함이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-106">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the available caching types are full caching, partial caching, and no caching.</span></span> <span data-ttu-id="48485-107">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]에서는 이러한 캐싱 유형 중 하나를 사용하도록 조회 변환을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-107">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], you can configure a Lookup transformation to use one of these caching types.</span></span> <span data-ttu-id="48485-108">부분 캐싱을 구현 하거나 캐싱을 하지 않는 방법에 대 한 자세한 내용은 [캐시 없음 또는 부분 캐시 모드로 조회 구현](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48485-108">For more information about how to implement partial caching or no caching, see [Implement a Lookup in No Cache or Partial Cache Mode](../../integration-services/data-flow/transformations/implement-a-lookup-in-no-cache-or-partial-cache-mode.md).</span></span> <span data-ttu-id="48485-109">전체 캐싱을 구현 하는 방법에 대 한 자세한 내용은 [캐시 연결 관리자를 사용 하 여 전체 캐시 모드에서 조회 변환 구현](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) 및 [OLE DB 연결 관리자를 사용 하 여 전체 캐시 모드에서 조회 변환 구현](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48485-109">For information about how to implement full caching, see [Implement a Lookup Transformation in Full Cache Mode Using the Cache Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-cache-connection-manager.md) and [Implement a Lookup Transformation in Full Cache Mode Using the OLE DB Connection Manager](../../integration-services/connection-manager/lookup-transformation-full-cache-mode-ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="48485-110">[!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)]에서는 조회 변환에 입력, 출력 및 오류 출력 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-110">In [!INCLUDE[ssISversion2005](../../includes/ssisversion2005-md.md)], the Lookup transformation had an input, an output, and an error output.</span></span> <span data-ttu-id="48485-111">참조 데이터 세트에 일치하는 항목이 있는 입력의 행은 출력에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="48485-111">Rows in the input that had matching entries in the reference dataset were handled by the output.</span></span> <span data-ttu-id="48485-112">일치하는 항목이 없는 입력의 행은 오류로 처리되어 오류 출력으로 리디렉션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-112">Rows in the input that did not have matching entries were treated as errors and could be redirected to the error output.</span></span> <span data-ttu-id="48485-113">[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]에서는 조회 변환에 일치 항목 출력과 불일치 항목 출력이라는 두 가지 유형의 출력이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-113">In [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], the Lookup transformation has two outputs: a match output and a no match output.</span></span>  
  
 <span data-ttu-id="48485-114">기본적으로 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 만든 조회 변환을 실행하면 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 에서 일치하는 항목이 없는 행을 오류로 간주하고 오류 출력으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-114">By default, when you run a Lookup transformation that was created in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] treats the rows without matching entries as errors and enables you to redirect the rows to an error output.</span></span> <span data-ttu-id="48485-115">또한 이러한 행을 오류가 아닌 것으로 간주하고 불일치 항목 출력으로 리디렉션할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48485-115">You have the option of configuring the Lookup transformation to treat the rows as non-errors and redirect the rows to the no match output.</span></span>  
  
 <span data-ttu-id="48485-116">자세한 내용은 [조회 변환 편집기 &#40;일반 페이지&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="48485-116">For more information, see [Lookup Transformation Editor &#40;General Page&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48485-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="48485-117">See Also</span></span>  
 [<span data-ttu-id="48485-118">조회 변환</span><span class="sxs-lookup"><span data-stu-id="48485-118">Lookup Transformation</span></span>](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
