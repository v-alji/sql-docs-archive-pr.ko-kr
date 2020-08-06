---
title: 유사 항목 조회 변환 편집기 (고급 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729631"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a><span data-ttu-id="2bcee-102">유사 항목 조회 변환 편집기(고급 탭)</span><span class="sxs-lookup"><span data-stu-id="2bcee-102">Fuzzy Lookup Transformation Editor (Advanced Tab)</span></span>
  <span data-ttu-id="2bcee-103">**유사 항목 조회 변환 편집기** 대화 상자의 **고급** 탭을 사용하여 유사 항목 조회 매개 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-103">Use the **Advanced** tab of the **Fuzzy Lookup Transformation Editor** dialog box to set parameters for the fuzzy lookup.</span></span>  
  
 <span data-ttu-id="2bcee-104">유사 항목 조회 변환에 대한 자세한 내용은 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2bcee-104">To learn more about the Fuzzy Lookup transformation, see [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2bcee-105">옵션</span><span class="sxs-lookup"><span data-stu-id="2bcee-105">Options</span></span>  
 <span data-ttu-id="2bcee-106">**조회당 출력에서 일치하는 최대 항목 수**</span><span class="sxs-lookup"><span data-stu-id="2bcee-106">**Maximum number of matches to output per lookup**</span></span>  
 <span data-ttu-id="2bcee-107">변환에서 각 입력 행에 대해 반환할 수 있는 일치하는 최대 항목 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-107">Specify the maximum number of matches the transformation can return for each input row.</span></span> <span data-ttu-id="2bcee-108">기본값은 **1**입니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-108">The default is **1**.</span></span>  
  
 <span data-ttu-id="2bcee-109">**유사성 임계값**</span><span class="sxs-lookup"><span data-stu-id="2bcee-109">**Similarity threshold**</span></span>  
 <span data-ttu-id="2bcee-110">슬라이더를 사용하여 구성 요소 수준에서 유사성 임계값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-110">Set the similarity threshold at the component level by using the slider.</span></span> <span data-ttu-id="2bcee-111">값이 1에 가까울수록 조회 값과 원본 값이 근접하여 일치 항목으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-111">The closer the value is to 1, the closer the resemblance of the lookup value to the source value must be to qualify as a match.</span></span> <span data-ttu-id="2bcee-112">임계값을 높이면 고려할 레코드 수가 감소하기 때문에 비교 속도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-112">Increasing the threshold can improve the speed of matching since fewer candidate records need to be considered.</span></span>  
  
 <span data-ttu-id="2bcee-113">**토큰 구분 기호**</span><span class="sxs-lookup"><span data-stu-id="2bcee-113">**Token delimiters**</span></span>  
 <span data-ttu-id="2bcee-114">변환에서 열 값을 토큰화하는 데 사용하는 구분 기호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcee-114">Specify the delimiters that the transformation uses to tokenize column values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcee-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bcee-115">See Also</span></span>  
 <span data-ttu-id="2bcee-116">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2bcee-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="2bcee-117">[유사 항목 조회 변환 편집기 &#40;참조 테이블 탭&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span><span class="sxs-lookup"><span data-stu-id="2bcee-117">[Fuzzy Lookup Transformation Editor &#40;Reference Table Tab&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md) </span></span>  
 [<span data-ttu-id="2bcee-118">유사 항목 조회 변환 편집기&#40;열 탭&#41;</span><span class="sxs-lookup"><span data-stu-id="2bcee-118">Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;</span></span>](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
