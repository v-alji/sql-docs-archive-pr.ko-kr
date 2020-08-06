---
title: 선택한 테이블 미리 보기 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741376"
---
# <a name="preview-selected-table-ssas"></a><span data-ttu-id="d137b-102">선택한 테이블 미리 보기(SSAS)</span><span class="sxs-lookup"><span data-stu-id="d137b-102">Preview Selected Table (SSAS)</span></span>
  <span data-ttu-id="d137b-103">**테이블 가져오기 마법사** 의 이 페이지에서는 선택된 테이블의 데이터를 미리 보고, 데이터 가져오기에 포함할 열을 선택하고, 선택된 열의 데이터를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-103">This page of the **Table Import Wizard** enables you to preview the data in the selected table, to select the columns to include in the data import, and to filter data in the selected columns.</span></span> <span data-ttu-id="d137b-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="d137b-105">이 페이지에는 테이블의 행이 일부만 표시되지만,</span><span class="sxs-lookup"><span data-stu-id="d137b-105">Not all the rows in the table are displayed.</span></span> <span data-ttu-id="d137b-106">사용자가 설정한 필터는 테이블을 가져올 때 해당 테이블의 모든 데이터에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-106">However, the filters that you set will be applied to all of the data in the table during import.</span></span>  
  
 <span data-ttu-id="d137b-107">Windows 인증을 사용하는 데이터 원본의 경우 현재 사용자의 자격 증명을 사용하여 미리 보기 및 필터 대화 상자에 표시된 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the data displayed in the Preview and Filter dialog.</span></span> <span data-ttu-id="d137b-108">기타 데이터 원본의 경우 연결 문자열에 제공된 자격 증명을 사용하여 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
 <span data-ttu-id="d137b-109">이 페이지에 데이터가 표시되었다고 해서 가져오기 작업이 반드시 성공하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-109">The appearance of data on this page does not guarantee import will succeed.</span></span> <span data-ttu-id="d137b-110">가장 정보 페이지에 지정된 사용자 이름에 선택한 데이터베이스를 읽을 수 있는 권한이 없는 경우 가져오기 작업이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-110">If the user name specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="d137b-111">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="d137b-111">UI element list</span></span>  
 <span data-ttu-id="d137b-112">**열 머리글의 확인란**</span><span class="sxs-lookup"><span data-stu-id="d137b-112">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="d137b-113">데이터 가져오기에 열을 포함하려면 이 확인란을 선택하고,</span><span class="sxs-lookup"><span data-stu-id="d137b-113">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="d137b-114">데이터 가져오기에서 열을 제거하려면 이 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-114">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="d137b-115">**열 머리글의 아래쪽 화살표 단추**</span><span class="sxs-lookup"><span data-stu-id="d137b-115">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="d137b-116">열의 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-116">Filter data in the column.</span></span>  
  
 <span data-ttu-id="d137b-117">**행 필터 지우기**</span><span class="sxs-lookup"><span data-stu-id="d137b-117">**Clear Row Filters**</span></span>  
 <span data-ttu-id="d137b-118">열의 데이터에 적용된 모든 필터를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d137b-118">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
