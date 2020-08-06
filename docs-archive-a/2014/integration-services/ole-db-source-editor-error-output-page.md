---
title: OLE DB 원본 편집기 (오류 출력 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsourceadapter.errorhandling.f1
helpviewer_keywords:
- OLE DB Source Editor
ms.assetid: 7737c6ae-c16b-4856-aa6e-5882640093b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ded87747f041a4d8451048d4ef4671b029125873
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660056"
---
# <a name="ole-db-source-editor-error-output-page"></a><span data-ttu-id="30e62-102">OLE DB 원본 편집기(오류 출력 페이지)</span><span class="sxs-lookup"><span data-stu-id="30e62-102">OLE DB Source Editor (Error Output Page)</span></span>
  <span data-ttu-id="30e62-103">**OLE DB 원본 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택하고 오류 출력 열에 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-103">Use the **Error Output** page of the **OLE DB Source Editor** dialog box to select error handling options and to set properties on error output columns.</span></span>  
  
 <span data-ttu-id="30e62-104">OLE DB 원본에 대한 자세한 내용은 [OLE DB Source](data-flow/ole-db-source.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="30e62-104">To learn more about the OLE DB source, see [OLE DB Source](data-flow/ole-db-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="30e62-105">옵션</span><span class="sxs-lookup"><span data-stu-id="30e62-105">Options</span></span>  
 <span data-ttu-id="30e62-106">**입/출력**</span><span class="sxs-lookup"><span data-stu-id="30e62-106">**Input/Output**</span></span>  
 <span data-ttu-id="30e62-107">데이터 원본의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-107">View the name of the data source.</span></span>  
  
 <span data-ttu-id="30e62-108">**열**</span><span class="sxs-lookup"><span data-stu-id="30e62-108">**Column**</span></span>  
 <span data-ttu-id="30e62-109">**OLE DB 원본 편집기** 대화 상자의 **연결 관리자**페이지에서 선택한 외부(원본) 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-109">View the external (source) columns that you selected on the **Connection Manager** page of the **OLE DB Source Editor**dialog box.</span></span>  
  
 <span data-ttu-id="30e62-110">**오류**</span><span class="sxs-lookup"><span data-stu-id="30e62-110">**Error**</span></span>  
 <span data-ttu-id="30e62-111">오류가 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-111">Specify what should happen when an error occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="30e62-112">**관련 항목:** [데이터 오류 처리](data-flow/error-handling-in-data.md)</span><span class="sxs-lookup"><span data-stu-id="30e62-112">**Related Topics:** [Error Handling in Data](data-flow/error-handling-in-data.md)</span></span>  
  
 <span data-ttu-id="30e62-113">**잘림**</span><span class="sxs-lookup"><span data-stu-id="30e62-113">**Truncation**</span></span>  
 <span data-ttu-id="30e62-114">잘림이 발생할 경우 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-114">Specify what should happen when a truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="30e62-115">**설명**</span><span class="sxs-lookup"><span data-stu-id="30e62-115">**Description**</span></span>  
 <span data-ttu-id="30e62-116">오류에 대한 설명을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-116">View the description of the error.</span></span>  
  
 <span data-ttu-id="30e62-117">**이 값을 선택한 셀에 설정**</span><span class="sxs-lookup"><span data-stu-id="30e62-117">**Set this value to selected cells**</span></span>  
 <span data-ttu-id="30e62-118">오류나 잘림 발생 시 선택한 모든 셀에 수행할 동작을 지정합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-118">Specify what should happen to all the selected cells when an error or truncation occurs: ignore the failure, redirect the row, or fail the component.</span></span>  
  
 <span data-ttu-id="30e62-119">**적용**</span><span class="sxs-lookup"><span data-stu-id="30e62-119">**Apply**</span></span>  
 <span data-ttu-id="30e62-120">선택한 셀에 오류 처리 옵션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="30e62-120">Apply the error handling option to the selected cells.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e62-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30e62-121">See Also</span></span>  
 <span data-ttu-id="30e62-122">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="30e62-122">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="30e62-123">[OLE DB 원본 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="30e62-123">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ole-db-source-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="30e62-124">[OLE DB 원본 편집기 &#40;열 페이지&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="30e62-124">[OLE DB Source Editor &#40;Columns Page&#41;](../../2014/integration-services/ole-db-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="30e62-125">[OLE DB 소스를 사용 하 여 데이터 추출](data-flow/extract-data-by-using-the-ole-db-source.md) </span><span class="sxs-lookup"><span data-stu-id="30e62-125">[Extract Data by Using the OLE DB Source](data-flow/extract-data-by-using-the-ole-db-source.md) </span></span>  
 [<span data-ttu-id="30e62-126">OLE DB 연결 관리자</span><span class="sxs-lookup"><span data-stu-id="30e62-126">OLE DB Connection Manager</span></span>](connection-manager/ole-db-connection-manager.md)  
  
  
