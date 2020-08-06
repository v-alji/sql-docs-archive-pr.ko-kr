---
title: '5단계: 플랫 파일 원본 추가 및 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5c95ce51-e0fe-4fc5-95eb-2945929f2b13
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 504cfb4bc722627eb8ee70ec1f2c562cef8f1f0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651125"
---
# <a name="step-5-adding-and-configuring-the-flat-file-source"></a><span data-ttu-id="e2bef-102">5단계: 플랫 파일 원본 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="e2bef-102">Step 5: Adding and Configuring the Flat File Source</span></span>
  <span data-ttu-id="e2bef-103">이 태스크에서는 플랫 파일 원본을 패키지에 추가하고 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-103">In this task, you will add and configure a Flat File source to your package.</span></span> <span data-ttu-id="e2bef-104">플랫 파일 원본은 플랫 파일 연결 관리자에서 정의된 메타데이터를 사용하여 변환 프로세스를 통해 플랫 파일에서 추출할 데이터 구조와 형식을 지정하는 데이터 흐름 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-104">A Flat File source is a data flow component that uses metadata defined by a Flat File connection manager to specify the format and structure of the data to be extracted from the flat file by a transform process.</span></span> <span data-ttu-id="e2bef-105">플랫 파일 원본은 플랫 파일 연결 관리자에서 제공된 파일 형식 정의를 사용하여 단일 플랫 파일에서 데이터를 추출하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-105">The Flat File source can be configured to extract data from a single flat file by using the file format definition provided by the Flat File connection manager.</span></span>  
  
 <span data-ttu-id="e2bef-106">이 자습서에서는 `Sample Flat File Source Data` 이전에 만든 연결 관리자를 사용 하도록 플랫 파일 원본을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-106">For this tutorial, you will configure the Flat File source to use the `Sample Flat File Source Data` connection manager that you previously created.</span></span>  
  
### <a name="to-add-a-flat-file-source-component"></a><span data-ttu-id="e2bef-107">플랫 파일 원본 구성 요소를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="e2bef-107">To add a Flat File Source component</span></span>  
  
1.  <span data-ttu-id="e2bef-108">데이터 흐름 태스크를 두 번 클릭 하거나 데이터 흐름 탭을 클릭 하 여 **데이터 흐름** 디자이너를 엽니다 `Extract Sample Currency Data` . **Data Flow tab**</span><span class="sxs-lookup"><span data-stu-id="e2bef-108">Open the **Data Flow** designer, either by double-clicking the `Extract Sample Currency Data` data flow task or by clicking the **Data Flow tab**.</span></span>  
  
2.  <span data-ttu-id="e2bef-109">**SSIS 도구 상자**에서 **기타 원본**을 확장한 다음 **플랫 파일 원본** 을 **데이터 흐름** 탭의 디자인 화면으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-109">In the **SSIS Toolbox**, expand **OtherSources**, and then drag a **Flat File Source** onto the design surface of the **Data Flow** tab.</span></span>  
  
3.  <span data-ttu-id="e2bef-110">**데이터 흐름** 디자인 화면에서 새로 추가한 **플랫 파일 원본을**마우스 오른쪽 단추로 클릭 하 고 이름 **바꾸기**를 클릭 한 다음 이름을로 변경 `Extract Sample Currency Data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-110">On the **Data Flow** design surface, right-click the newly added **Flat File Source**, click **Rename**, and change the name to `Extract Sample Currency Data`.</span></span>  
  
4.  <span data-ttu-id="e2bef-111">플랫 파일 원본을 두 번 클릭하여 플랫 파일 원본 편집기 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-111">Double-click the Flat File source to open the Flat File Source Editor dialog box.</span></span>  
  
5.  <span data-ttu-id="e2bef-112">**플랫 파일 연결 관리자** 상자에서를 선택 `Sample Flat File Source Data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-112">In the **Flat file connection manager** box, select `Sample Flat File Source Data`.</span></span>  
  
6.  <span data-ttu-id="e2bef-113">**열** 을 클릭하고 열 이름이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-113">Click **Columns** and verify that the names of the columns are correct.</span></span>  
  
7.  <span data-ttu-id="e2bef-114">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-114">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="e2bef-115">플랫 파일 원본을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-115">Right-click the Flat File source and click **Properties**.</span></span>  
  
9. <span data-ttu-id="e2bef-116">속성 창에서 `LocaleID` 속성이 **영어 (미국)** 로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2bef-116">In the Properties window, verify that the `LocaleID` property is set to **English (United States)**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e2bef-117">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="e2bef-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e2bef-118">6단계: 조회 변환 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="e2bef-118">Step 6: Adding and Configuring the Lookup Transformations</span></span>](lesson-1-6-adding-and-configuring-the-lookup-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="e2bef-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2bef-119">See Also</span></span>  
 <span data-ttu-id="e2bef-120">[플랫 파일 원본](data-flow/flat-file-source.md) </span><span class="sxs-lookup"><span data-stu-id="e2bef-120">[Flat File Source](data-flow/flat-file-source.md) </span></span>  
 [<span data-ttu-id="e2bef-121">플랫 파일 연결 관리자 편집기&#40;일반 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="e2bef-121">Flat File Connection Manager Editor &#40;General Page&#41;</span></span>](general-page-of-integration-services-designers-options.md)  
  
  
