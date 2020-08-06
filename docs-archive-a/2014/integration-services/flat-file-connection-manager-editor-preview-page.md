---
title: 플랫 파일 연결 관리자 편집기 (미리 보기 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.preview.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: de47ea98-135e-4730-900e-dac629848798
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b0f71b347bc943216a4b309cc58202ed8ab9183e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647153"
---
# <a name="flat-file-connection-manager-editor-preview-page"></a><span data-ttu-id="fb9f9-102">플랫 파일 연결 관리자 편집기(미리 보기 페이지)</span><span class="sxs-lookup"><span data-stu-id="fb9f9-102">Flat File Connection Manager Editor (Preview Page)</span></span>
  <span data-ttu-id="fb9f9-103">**플랫 파일 연결 관리자 편집기** 대화 상자의 **미리 보기** 노드를 사용하여 원본 파일의 내용을 테이블 형식으로 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-103">Use the **Preview** node of the **Flat File Connection Manager Editor** dialog box to view the contents of the source file in a tabular format.</span></span>  
  
 <span data-ttu-id="fb9f9-104">플랫 파일 연결 관리자에 대한 자세한 내용은 [Flat File Connection Manager](connection-manager/file-connection-manager.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-104">To learn more about the Flat File connection manager, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="fb9f9-105">옵션</span><span class="sxs-lookup"><span data-stu-id="fb9f9-105">Options</span></span>  
 <span data-ttu-id="fb9f9-106">**연결 관리자 이름**</span><span class="sxs-lookup"><span data-stu-id="fb9f9-106">**Connection manager name**</span></span>  
 <span data-ttu-id="fb9f9-107">워크플로의 플랫 파일 연결에 고유한 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-107">Provide a unique name for the Flat File connection in the workflow.</span></span> <span data-ttu-id="fb9f9-108">제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-108">The name provided will be displayed within [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="fb9f9-109">**설명**</span><span class="sxs-lookup"><span data-stu-id="fb9f9-109">**Description**</span></span>  
 <span data-ttu-id="fb9f9-110">연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-110">Describe the connection.</span></span> <span data-ttu-id="fb9f9-111">해당 연결의 용도를 설명하여 패키지를 이해하기 쉽고 유지 관리하기 편하도록 만드는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-111">As a best practice, describe the connection in terms of its purpose, to make packages self-documenting and easier to maintain.</span></span>  
  
 <span data-ttu-id="fb9f9-112">**건너뛸 데이터 행**</span><span class="sxs-lookup"><span data-stu-id="fb9f9-112">**Data rows to skip**</span></span>  
 <span data-ttu-id="fb9f9-113">플랫 파일의 시작 부분에서 건너뛸 행 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-113">Specify how many rows to skip at the beginning of the flat file.</span></span>  
  
 <span data-ttu-id="fb9f9-114">**새로 고침**</span><span class="sxs-lookup"><span data-stu-id="fb9f9-114">**Refresh**</span></span>  
 <span data-ttu-id="fb9f9-115">**새로 고침**을 클릭하여 건너뛸 행 수의 변경 결과를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-115">View the effect of changing the number of rows to skip by clicking **Refresh**.</span></span> <span data-ttu-id="fb9f9-116">이 단추는 다른 연결 옵션을 변경한 후에만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-116">This button only becomes visible after you have changed other connection options.</span></span>  
  
 <span data-ttu-id="fb9f9-117">**행 미리 보기**</span><span class="sxs-lookup"><span data-stu-id="fb9f9-117">**Preview rows**</span></span>  
 <span data-ttu-id="fb9f9-118">선택한 옵션을 사용하여 열과 행으로 구분된 플랫 파일로 샘플 데이터를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="fb9f9-118">View sample data in the flat file, divided into columns and rows according to the options you have selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9f9-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fb9f9-119">See Also</span></span>  
 <span data-ttu-id="fb9f9-120">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="fb9f9-120">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="fb9f9-121">[플랫 파일 연결 관리자 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="fb9f9-121">[Flat File Connection Manager Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="fb9f9-122">[플랫 파일 연결 관리자 편집기 &#40;열 페이지&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="fb9f9-122">[Flat File Connection Manager Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md) </span></span>  
 [<span data-ttu-id="fb9f9-123">플랫 파일 연결 관리자 편집기&#40;고급 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="fb9f9-123">Flat File Connection Manager Editor &#40;Advanced Page&#41;</span></span>](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
  
