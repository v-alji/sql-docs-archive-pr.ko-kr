---
title: 용어 추출 변환 편집기 (제외 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bc4b0401a1dd27111d0498e9e0d848c80da1742
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660680"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a><span data-ttu-id="6a342-102">용어 추출 변환 편집기(제외 탭)</span><span class="sxs-lookup"><span data-stu-id="6a342-102">Term Extraction Transformation Editor (Exclusion Tab)</span></span>
  <span data-ttu-id="6a342-103">**용어 추출 변환 편집기** 대화 상자의 **제외** 탭을 사용하여 제외 테이블에 대한 연결을 설정하고 제외 용어를 포함하는 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-103">Use the **Exclusion** tab of the **Term Extraction Transformation Editor** dialog box to set up a connection to an exclusion table and specify the columns that contain exclusion terms.</span></span>  
  
 <span data-ttu-id="6a342-104">용어 추출 변환에 대한 자세한 내용은 [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6a342-104">To learn more about the Term Extraction transformation, see [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6a342-105">옵션</span><span class="sxs-lookup"><span data-stu-id="6a342-105">Options</span></span>  
 <span data-ttu-id="6a342-106">**제외 용어 사용**</span><span class="sxs-lookup"><span data-stu-id="6a342-106">**Use exclusion terms**</span></span>  
 <span data-ttu-id="6a342-107">제외 용어를 포함하는 열을 지정하여 용어 추출 중 특정 용어를 제외할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-107">Indicate whether to exclude specific terms during term extraction by specifying a column that contains exclusion terms.</span></span> <span data-ttu-id="6a342-108">용어를 제외하기로 선택하는 경우 다음 원본 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-108">You must specify the following source properties if you choose to exclude terms.</span></span>  
  
 <span data-ttu-id="6a342-109">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="6a342-109">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="6a342-110">기존 OLE DB 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-110">Select an existing OLE DB connection manager, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="6a342-111">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="6a342-111">**New**</span></span>  
 <span data-ttu-id="6a342-112">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 데이터베이스에 대한 새 연결을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-112">Create a new connection to a database by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="6a342-113">**테이블 또는 뷰**</span><span class="sxs-lookup"><span data-stu-id="6a342-113">**Table or view**</span></span>  
 <span data-ttu-id="6a342-114">제외 용어를 포함하는 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-114">Select the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="6a342-115">**열**</span><span class="sxs-lookup"><span data-stu-id="6a342-115">**Column**</span></span>  
 <span data-ttu-id="6a342-116">제외 용어를 포함하는 테이블 또는 뷰의 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-116">Select the column in the table or view that contains the exclusion terms.</span></span>  
  
 <span data-ttu-id="6a342-117">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="6a342-117">**Configure Error Output**</span></span>  
 <span data-ttu-id="6a342-118">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 발생의 원인이 되는 행에 대한 오류 처리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a342-118">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a342-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a342-119">See Also</span></span>  
 <span data-ttu-id="6a342-120">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="6a342-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="6a342-121">[용어 추출 변환 편집기 &#40;용어 추출 탭&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span><span class="sxs-lookup"><span data-stu-id="6a342-121">[Term Extraction Transformation Editor &#40;Term Extraction Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md) </span></span>  
 <span data-ttu-id="6a342-122">[용어 추출 변환 편집기 &#40;고급 탭&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="6a342-122">[Term Extraction Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="6a342-123">용어 조회 변환</span><span class="sxs-lookup"><span data-stu-id="6a342-123">Term Lookup Transformation</span></span>](data-flow/transformations/lookup-transformation.md)  
  
  
