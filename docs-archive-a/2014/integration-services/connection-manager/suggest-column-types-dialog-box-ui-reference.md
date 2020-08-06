---
title: 열 유형 제안 대화 상자 UI 참조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.suggestdatatypes.f1
ms.assetid: 8d5652e0-cf57-483f-828b-10f00c08418b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbca2a3186a58b1148eb9627825fdfddf334339
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741180"
---
# <a name="suggest-column-types-dialog-box-ui-reference"></a><span data-ttu-id="3dafe-102">열 유형 제안 대화 상자 UI 참조</span><span class="sxs-lookup"><span data-stu-id="3dafe-102">Suggest Column Types Dialog Box UI Reference</span></span>
  <span data-ttu-id="3dafe-103">**열 유형 제안** 대화 상자를 사용하여 파일 내용의 샘플링을 기반으로 플랫 파일 연결 관리자에 있는 열의 데이터 형식과 길이를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-103">Use the **Suggest Column Types** dialog box to identify the data type and length of columns in a Flat File Connection Manager based on a sampling of the file content.</span></span>  
  
 <span data-ttu-id="3dafe-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서 사용하는 데이터 형식에 대한 자세한 내용은 [Integration Services 데이터 형식](../data-flow/integration-services-data-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3dafe-104">To learn more about the data types used by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="3dafe-105">옵션</span><span class="sxs-lookup"><span data-stu-id="3dafe-105">Options</span></span>  
 <span data-ttu-id="3dafe-106">**행 수**</span><span class="sxs-lookup"><span data-stu-id="3dafe-106">**Number of rows**</span></span>  
 <span data-ttu-id="3dafe-107">알고리즘에서 사용하는 샘플의 행 수를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-107">Type or select the number of rows in the sample that the algorithm uses.</span></span>  
  
 <span data-ttu-id="3dafe-108">**가장 작은 정수 데이터 형식 제안**</span><span class="sxs-lookup"><span data-stu-id="3dafe-108">**Suggest the smallest integer data type**</span></span>  
 <span data-ttu-id="3dafe-109">평가를 건너뛰려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-109">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="3dafe-110">이 확인란이 선택되어 있으면 정수 데이터를 포함하는 열에 대해 가능한 가장 작은 정수 데이터 형식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-110">If selected, determines the smallest possible integer data type for columns that contain integral numeric data.</span></span>  
  
 <span data-ttu-id="3dafe-111">**가장 작은 실수 데이터 형식 제안**</span><span class="sxs-lookup"><span data-stu-id="3dafe-111">**Suggest the smallest real data type**</span></span>  
 <span data-ttu-id="3dafe-112">평가를 건너뛰려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-112">Clear this check box to skip the assessment.</span></span> <span data-ttu-id="3dafe-113">이 확인란이 선택되어 있으면 실수 데이터를 포함하는 열에서 보다 작은 실수 데이터 형식인 DT_R4를 사용할 수 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-113">If selected, determines whether columns that contain real numeric data can use the smaller real data type, DT_R4.</span></span>  
  
 <span data-ttu-id="3dafe-114">**다음 값을 사용하여 부울 열 식별**</span><span class="sxs-lookup"><span data-stu-id="3dafe-114">**Identify Boolean columns using the following values**</span></span>  
 <span data-ttu-id="3dafe-115">부울 값 True와 False로 사용할 값 두 개를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-115">Type the two values that you want to use as the Boolean values true and false.</span></span> <span data-ttu-id="3dafe-116">쉼표로 값을 구분해야 하며 첫 번째 값이 True를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-116">The values must be separated by a comma, and the first value represents True.</span></span>  
  
 <span data-ttu-id="3dafe-117">**문자열 열 패딩**</span><span class="sxs-lookup"><span data-stu-id="3dafe-117">**Pad string columns**</span></span>  
 <span data-ttu-id="3dafe-118">문자열 패딩을 사용하려면 이 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-118">Select this check box to enable string padding.</span></span>  
  
 <span data-ttu-id="3dafe-119">**패딩 비율**</span><span class="sxs-lookup"><span data-stu-id="3dafe-119">**Percent padding**</span></span>  
 <span data-ttu-id="3dafe-120">문자 데이터 형식 열의 길이에 추가할 열 길이의 비율을 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-120">Type or select the percentage of the column lengths by which to increase the length of columns for character data types.</span></span> <span data-ttu-id="3dafe-121">비율은 정수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3dafe-121">The percentage must be an integer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dafe-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3dafe-122">See Also</span></span>  
 <span data-ttu-id="3dafe-123">[Integration Services 오류 및 메시지 참조](../integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3dafe-123">[Integration Services Error and Message Reference](../integration-services-error-and-message-reference.md) </span></span>  
 [<span data-ttu-id="3dafe-124">플랫 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="3dafe-124">Flat File Connection Manager</span></span>](file-connection-manager.md)  
  
  
