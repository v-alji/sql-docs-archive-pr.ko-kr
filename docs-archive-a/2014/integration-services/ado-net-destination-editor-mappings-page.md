---
title: ADO NET 대상 편집기 (매핑 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.mappings.f1
ms.assetid: 842d075f-8b7a-457c-a1a1-a7acbe10e9b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e7a2397e4e2d16e6eeca93d41f5127dfde4c35e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638959"
---
# <a name="ado-net-destination-editor-mappings-page"></a><span data-ttu-id="7d3d9-102">ADO NET 대상 편집기(매핑 페이지)</span><span class="sxs-lookup"><span data-stu-id="7d3d9-102">ADO NET Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="7d3d9-103">**ADO NET 대상 편집기** 대화 상자의 **매핑** 페이지를 사용하여 입력 열을 대상 열에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-103">Use the **Mappings** page of the **ADO NET Destination Editor** dialog box to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="7d3d9-104">ADO NET 대상에 대한 자세한 내용은 [ADO NET Destination](data-flow/ado-net-destination.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="7d3d9-105">**매핑 페이지를 열려면**</span><span class="sxs-lookup"><span data-stu-id="7d3d9-105">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="7d3d9-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 ADO NET 대상이 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 패키지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="7d3d9-107">**데이터 흐름** 탭에서 ADO NET 대상을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="7d3d9-108">**ADO NET 대상 편집기**에서 **매핑**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-108">In the **ADO NET Destination Editor**, click **Mappings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="7d3d9-109">옵션</span><span class="sxs-lookup"><span data-stu-id="7d3d9-109">Options</span></span>  
 <span data-ttu-id="7d3d9-110">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="7d3d9-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="7d3d9-111">사용 가능한 입력 열 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-111">View the list of available input columns.</span></span> <span data-ttu-id="7d3d9-112">끌어서 놓기 작업을 사용하여 테이블에서 사용 가능한 입력 열을 대상 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-112">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="7d3d9-113">**사용 가능한 대상 열**</span><span class="sxs-lookup"><span data-stu-id="7d3d9-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="7d3d9-114">사용 가능한 대상 열의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-114">View the list of available destination columns.</span></span> <span data-ttu-id="7d3d9-115">끌어서 놓기 작업을 사용하여 테이블에서 사용 가능한 대상 열을 입력 열에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-115">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="7d3d9-116">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="7d3d9-116">**Input Column**</span></span>  
 <span data-ttu-id="7d3d9-117">선택한 입력 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-117">View the input columns that you selected.</span></span> <span data-ttu-id="7d3d9-118">출력에서 열을 제외하는 **\<ignore>** 를 선택하여 매핑을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-118">You can remove mappings by selecting **\<ignore>** to exclude columns from the output.</span></span>  
  
 <span data-ttu-id="7d3d9-119">**대상 열**</span><span class="sxs-lookup"><span data-stu-id="7d3d9-119">**Destination Column**</span></span>  
 <span data-ttu-id="7d3d9-120">매핑 여부에 관계없이 사용 가능한 각 대상 열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7d3d9-120">View each available destination column, regardless of whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3d9-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7d3d9-121">See Also</span></span>  
 <span data-ttu-id="7d3d9-122">[ADO NET 대상 편집기 &#40;연결 관리자 페이지&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="7d3d9-122">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 [<span data-ttu-id="7d3d9-123">ADO NET 대상 편집기&#40;오류 출력 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="7d3d9-123">ADO NET Destination Editor &#40;Error Output Page&#41;</span></span>](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)  
  
  
