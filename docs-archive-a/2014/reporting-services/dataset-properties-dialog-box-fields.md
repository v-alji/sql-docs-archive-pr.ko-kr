---
title: 데이터 집합 속성 대화 상자, 필드 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1b9d315f85751c0f73896e809a522613fefece5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647532"
---
# <a name="dataset-properties-dialog-box-fields"></a><span data-ttu-id="df542-102">데이터 세트 속성 대화 상자, 필드</span><span class="sxs-lookup"><span data-stu-id="df542-102">Dataset Properties Dialog Box, Fields</span></span>
  <span data-ttu-id="df542-103">**데이터 세트 속성** 대화 상자에서 **필드**를 선택하여 보고서 데이터 세트의 필드 컬렉션을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df542-103">Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset.</span></span> <span data-ttu-id="df542-104">필드 목록은 자동으로 채워지지만 **필드** 를 사용하여 쿼리와 계산 필드를 추가, 편집 및 삭제할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df542-104">The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.</span></span>  
  
## <a name="options"></a><span data-ttu-id="df542-105">옵션</span><span class="sxs-lookup"><span data-stu-id="df542-105">Options</span></span>  
 <span data-ttu-id="df542-106">**추가**</span><span class="sxs-lookup"><span data-stu-id="df542-106">**Add**</span></span>  
 <span data-ttu-id="df542-107">데이터 세트에 새 쿼리 필드나 계산 필드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-107">Add a new query field or calculated field to the dataset.</span></span>  
  
 <span data-ttu-id="df542-108">**삭제**</span><span class="sxs-lookup"><span data-stu-id="df542-108">**Delete**</span></span>  
 <span data-ttu-id="df542-109">선택한 필드를 데이터 세트에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-109">Delete the selected field from the dataset.</span></span>  
  
 <span data-ttu-id="df542-110">**필드 이름**</span><span class="sxs-lookup"><span data-stu-id="df542-110">**Field Name**</span></span>  
 <span data-ttu-id="df542-111">필드의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-111">Type a name for the field.</span></span> <span data-ttu-id="df542-112">필드는 데이터 세트 내에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-112">The field must be unique within the dataset.</span></span> <span data-ttu-id="df542-113">데이터 세트 쿼리의 기존 필드에 대해서는 각각 이름이 미리 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="df542-113">For each existing field in the dataset query, the name is pre-populated.</span></span>  
  
 <span data-ttu-id="df542-114">**필드 원본**</span><span class="sxs-lookup"><span data-stu-id="df542-114">**Field Source**</span></span>  
 <span data-ttu-id="df542-115">필드의 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-115">Enter a value for the field.</span></span>  
  
 <span data-ttu-id="df542-116">계산 필드의 경우 필드 원본은 데이터 세트 쿼리 또는 사용자가 만든 식으로 검색된 기존 필드의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-116">For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create.</span></span> <span data-ttu-id="df542-117">예를 들어 Sales라는 쿼리 필드의 값에 10을 곱한 값을 표시하는 필드를 만들려면 `=10 * Fields!Sales.Value`식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-117">For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.</span></span>  
  
 <span data-ttu-id="df542-118">쿼리 필드의 경우 필드 원본은 데이터 세트 쿼리로 검색된 기존 필드의 이름이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-118">For a query field, the field source must be the name of an existing field retrieved by the dataset query.</span></span>  
  
 <span data-ttu-id="df542-119">**식(fx)**</span><span class="sxs-lookup"><span data-stu-id="df542-119">**Expression (fx)**</span></span>  
 <span data-ttu-id="df542-120">계산 필드의 식을 추가하거나 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="df542-120">Add or change an expression for the calculated field.</span></span> <span data-ttu-id="df542-121">이 단추는 **추가** 를 클릭하고 **계산 필드**를 선택했을 때만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="df542-121">This button only appears when you click **Add** and select **Calculated Field**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df542-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df542-122">See Also</span></span>  
 <span data-ttu-id="df542-123">[데이터 세트 필드 컬렉션&#40;보고서 작성기 및 SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df542-123">[Dataset Fields Collection &#40;Report Builder and SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="df542-124">[보고서 &#40;보고서 작성기 및 SSRS&#41;에 데이터를 추가 합니다.](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df542-124">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 [<span data-ttu-id="df542-125">식&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="df542-125">Expressions &#40;Report Builder and SSRS&#41;</span></span>](report-design/expressions-report-builder-and-ssrs.md)  
  
  
