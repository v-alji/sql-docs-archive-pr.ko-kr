---
title: 플랫 파일 원본 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c1693c001dad2c8e90211b065eda208c42a07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647140"
---
# <a name="flat-file-source-editor-connection-manager-page"></a><span data-ttu-id="8e6ad-102">플랫 파일 원본 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="8e6ad-102">Flat File Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="8e6ad-103">**플랫 파일 원본 편집기** 대화 상자의 **연결 관리자** 페이지를 사용하여 플랫 파일 원본이 사용할 연결 관리자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-103">Use the **Connection Manager** page of the **Flat File Source Editor** dialog box to select the connection manager that the Flat File source will use.</span></span> <span data-ttu-id="8e6ad-104">플랫 파일 원본은 구분 기호로 분리된 텍스트 파일, 고정 폭 텍스트 파일 또는 혼합 형식의 텍스트 파일에서 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-104">The Flat File source reads data from a text file, which can be in a delimited, fixed width, or mixed format.</span></span>  
  
 <span data-ttu-id="8e6ad-105">플랫 파일 원본은 다음과 같은 연결 관리자 유형 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-105">A Flat File source can use one of the following types of connection managers:</span></span>  
  
-   <span data-ttu-id="8e6ad-106">원본이 단일 플랫 파일인 경우 플랫 파일 연결 관리자.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-106">A Flat File connection manager if the source is a single flat file.</span></span> <span data-ttu-id="8e6ad-107">자세한 내용은 [Flat File Connection Manager](connection-manager/file-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-107">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
-   <span data-ttu-id="8e6ad-108">원본이 다중 플랫 파일이고 데이터 흐름 태스크가 For 루프 컨테이너와 같은 루프 컨테이너 내부에 있는 경우 다중 플랫 파일 연결 관리자.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-108">A Multiple Flat Files connection manager if the source is multiple flat files and the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="8e6ad-109">각 컨테이너 루프에서 플랫 파일 원본은 다중 플랫 파일 연결 관리자가 제공하는 다음 파일 이름에서 데이터를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-109">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span> <span data-ttu-id="8e6ad-110">자세한 내용은 [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-110">For more information, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
 <span data-ttu-id="8e6ad-111">플랫 파일 원본에 대한 자세한 내용은 [Flat File Source](data-flow/flat-file-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-111">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e6ad-112">옵션</span><span class="sxs-lookup"><span data-stu-id="8e6ad-112">Options</span></span>  
 <span data-ttu-id="8e6ad-113">**플랫 파일 연결 관리자**</span><span class="sxs-lookup"><span data-stu-id="8e6ad-113">**Flat file connection manager**</span></span>  
 <span data-ttu-id="8e6ad-114">목록에서 기존 연결 관리자를 선택하거나 **새로 만들기**를 클릭하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-114">Select an existing connection manager from the list, or create a new connection manager by clicking **New**.</span></span>  
  
 <span data-ttu-id="8e6ad-115">**새로 만들기**</span><span class="sxs-lookup"><span data-stu-id="8e6ad-115">**New**</span></span>  
 <span data-ttu-id="8e6ad-116">**플랫 파일 연결 관리자 편집기** 대화 상자를 사용하여 새 연결 관리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-116">Create a new connection manager by using the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="8e6ad-117">**원본의 Null 값을 데이터 흐름의 Null 값으로 유지**</span><span class="sxs-lookup"><span data-stu-id="8e6ad-117">**Retain null values from the source as null values in the data flow**</span></span>  
 <span data-ttu-id="8e6ad-118">데이터를 추출할 때 Null 값을 유지할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-118">Specify whether to keep null values when data is extracted.</span></span> <span data-ttu-id="8e6ad-119">이 속성의 기본값은 **false**입니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-119">The default value of this property is **false**.</span></span> <span data-ttu-id="8e6ad-120">이 값이 f`alse`이면 플랫 파일 원본이 원본 데이터의 Null 값을 각 열에 적합한 기본값으로 바꿉니다. 예를 들어 문자열 열의 경우 빈 문자열로 바꾸고 숫자 열의 경우 0으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-120">When this value is f`alse`, the Flat File source replaces null values from the source data with appropriate default values for each column, such as empty strings for string columns and zero for numeric columns.</span></span>  
  
 <span data-ttu-id="8e6ad-121">**미리 보기**</span><span class="sxs-lookup"><span data-stu-id="8e6ad-121">**Preview**</span></span>  
 <span data-ttu-id="8e6ad-122">**데이터 보기** 대화 상자를 사용하여 결과를 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-122">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="8e6ad-123">미리 보기에는 최대 200개의 행이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e6ad-123">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6ad-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e6ad-124">See Also</span></span>  
 <span data-ttu-id="8e6ad-125">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="8e6ad-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="8e6ad-126">[플랫 파일 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="8e6ad-126">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="8e6ad-127">[플랫 파일 원본 편집기 &#40;오류 출력 페이지&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="8e6ad-127">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="8e6ad-128">플랫 파일 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="8e6ad-128">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
