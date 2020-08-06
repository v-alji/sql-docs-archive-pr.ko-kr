---
title: 용어 조회 변환 편집기 (참조 테이블 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.referencetable.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 86ccec6d-615b-4f84-9226-ff80d8012f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f76f15d894896e70139ef80cb2ebad7004ef47ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660676"
---
# <a name="term-lookup-transformation-editor-reference-table-tab"></a><span data-ttu-id="4e477-102">용어 조회 변환 편집기(참조 테이블 탭)</span><span class="sxs-lookup"><span data-stu-id="4e477-102">Term Lookup Transformation Editor (Reference Table Tab)</span></span>
  <span data-ttu-id="4e477-103">**용어 조회 변환 편집기** 대화 상자의 **참조 테이블** 탭을 사용하여 참조(조회) 테이블에 대한 연결을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-103">Use the **Reference Table** tab of the **Term Lookup Transformation Editor** dialog box to specify the connection to the reference (lookup) table.</span></span>  
  
 <span data-ttu-id="4e477-104">용어 조회 변환에 대한 자세한 내용은 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4e477-104">To learn more about the Term Lookup transformation, see [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4e477-105">옵션</span><span class="sxs-lookup"><span data-stu-id="4e477-105">Options</span></span>  
 <span data-ttu-id="4e477-106">**캐시 없음**</span><span class="sxs-lookup"><span data-stu-id="4e477-106">**OLE DB connection manager**</span></span>  
 <span data-ttu-id="4e477-107">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-107">Select an existing connection manager from the list, or create a new connection by clicking **New**.</span></span>  
  
 <span data-ttu-id="4e477-108">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="4e477-108">**New**</span></span>  
 <span data-ttu-id="4e477-109">**OLE DB 연결 관리자 구성** 대화 상자를 사용하여 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-109">Create a new connection by using the **Configure OLE DB Connection Manager** dialog box.</span></span>  
  
 <span data-ttu-id="4e477-110">**참조 테이블 이름**</span><span class="sxs-lookup"><span data-stu-id="4e477-110">**Reference table name**</span></span>  
 <span data-ttu-id="4e477-111">목록에서 항목을 골라 데이터베이스의 조회 테이블 또는 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-111">Select a lookup table or view from the database by selecting an item from the list.</span></span> <span data-ttu-id="4e477-112">테이블 또는 뷰는 원본 열의 텍스트와 비교할 수 있는 기존 용어 목록이 있는 열을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-112">The table or view should contain a column with an existing list of terms that the text in the source column can be compared to.</span></span>  
  
 <span data-ttu-id="4e477-113">**오류 출력 구성**</span><span class="sxs-lookup"><span data-stu-id="4e477-113">**Configure Error Output**</span></span>  
 <span data-ttu-id="4e477-114">[오류 출력 구성](../../2014/integration-services/configure-error-output.md) 대화 상자를 사용하여 오류 발생의 원인이 되는 행에 대한 오류 처리 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e477-114">Use the [Configure Error Output](../../2014/integration-services/configure-error-output.md) dialog box to specify error handling options for rows that cause errors.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e477-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e477-115">See Also</span></span>  
 <span data-ttu-id="4e477-116">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4e477-116">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="4e477-117">[용어 조회 변환 편집기 &#40;용어 조회 탭&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span><span class="sxs-lookup"><span data-stu-id="4e477-117">[Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-term-lookup-tab.md) </span></span>  
 <span data-ttu-id="4e477-118">[용어 조회 변환 편집기 &#40;고급 탭&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span><span class="sxs-lookup"><span data-stu-id="4e477-118">[Term Lookup Transformation Editor &#40;Advanced Tab&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md) </span></span>  
 [<span data-ttu-id="4e477-119">용어 추출 변환</span><span class="sxs-lookup"><span data-stu-id="4e477-119">Term Extraction Transformation</span></span>](data-flow/transformations/term-extraction-transformation.md)  
  
  
