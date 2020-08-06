---
title: Union All 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.unionalltransformation.f1
helpviewer_keywords:
- Union All Transformation Editor
ms.assetid: 32fbc1c1-da83-4684-9479-31fc3e2df98c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a7e84c106767aa897b2e419b51ca5b5c538501cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647738"
---
# <a name="union-all-transformation-editor"></a><span data-ttu-id="a6e81-102">UNION ALL 변환 편집기</span><span class="sxs-lookup"><span data-stu-id="a6e81-102">Union All Transformation Editor</span></span>
  <span data-ttu-id="a6e81-103">**UNION ALL 변환 편집기** 대화 상자를 사용하여 여러 개의 입력 행 집합을 단일 출력 행 집합으로 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-103">Use the **Union All Transformation Editor** dialog box to merge several input rowsets into a single output rowset.</span></span> <span data-ttu-id="a6e81-104">Union All 변환을 데이터 흐름에 포함하면 여러 데이터 흐름의 데이터를 병합하고, Union All 변환을 중첩하여 복잡한 데이터 세트를 만들고, 데이터의 오류를 수정하고, 행을 다시 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-104">By including the Union All transformation in a data flow, you can merge data from multiple data flows, create complex datasets by nesting Union All transformations, and re-merge rows after you correct errors in the data.</span></span>  
  
 <span data-ttu-id="a6e81-105">UNION ALL 변환에 대한 자세한 내용은 [Union All Transformation](data-flow/transformations/union-all-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="a6e81-105">To learn more about the Union All transformation, see [Union All Transformation](data-flow/transformations/union-all-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a6e81-106">옵션</span><span class="sxs-lookup"><span data-stu-id="a6e81-106">Options</span></span>  
 <span data-ttu-id="a6e81-107">**출력 열 이름**</span><span class="sxs-lookup"><span data-stu-id="a6e81-107">**Output Column Name**</span></span>  
 <span data-ttu-id="a6e81-108">각 열의 별칭을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-108">Type an alias for each column.</span></span> <span data-ttu-id="a6e81-109">기본값은 첫 번째(참조) 입력의 입력 열 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-109">The default is the name of the input column from the first (reference) input; however, you can choose any unique, descriptive name.</span></span>  
  
 <span data-ttu-id="a6e81-110">**UNION ALL 입력 1**</span><span class="sxs-lookup"><span data-stu-id="a6e81-110">**Union All Input 1**</span></span>  
 <span data-ttu-id="a6e81-111">첫 번째(참조) 입력의 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-111">Select from the list of available input columns in the first (reference) input.</span></span> <span data-ttu-id="a6e81-112">매핑된 열의 메타데이터가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-112">The metadata of mapped columns must match.</span></span>  
  
 <span data-ttu-id="a6e81-113">**UNION ALL 입력 n**</span><span class="sxs-lookup"><span data-stu-id="a6e81-113">**Union All Input n**</span></span>  
 <span data-ttu-id="a6e81-114">두 번째 및 추가 입력의 사용 가능한 입력 열 목록에서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-114">Select from the list of available input columns in the second and additional inputs.</span></span> <span data-ttu-id="a6e81-115">매핑된 열의 메타데이터가 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6e81-115">The metadata of mapped columns must match.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e81-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6e81-116">See Also</span></span>  
 <span data-ttu-id="a6e81-117">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="a6e81-117">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="a6e81-118">[Union All 변환을 사용 하 여 데이터 병합](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a6e81-118">[Merge Data by Using the Union All Transformation](data-flow/transformations/merge-data-by-using-the-union-all-transformation.md) </span></span>  
 <span data-ttu-id="a6e81-119">[병합 변환](data-flow/transformations/merge-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="a6e81-119">[Merge Transformation](data-flow/transformations/merge-transformation.md) </span></span>  
 [<span data-ttu-id="a6e81-120">병합 조인 변환</span><span class="sxs-lookup"><span data-stu-id="a6e81-120">Merge Join Transformation</span></span>](data-flow/transformations/merge-join-transformation.md)  
  
  
