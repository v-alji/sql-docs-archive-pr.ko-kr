---
title: 가져오기 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importing.f1
ms.assetid: f1681be4-c543-4e77-875d-b13eeb75cf77
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95ea60385014e5ca8b998b986a66c384f7151081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660186"
---
# <a name="importing-ssas"></a><span data-ttu-id="c9c6e-102">가져오기(SSAS)</span><span class="sxs-lookup"><span data-stu-id="c9c6e-102">Importing (SSAS)</span></span>
  <span data-ttu-id="c9c6e-103">**테이블 가져오기 마법사** 의 이 페이지에서는 가져오기 작업의 진행률을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-103">This page of the **Table Import Wizard** enables you to view the progress of the import operation.</span></span> <span data-ttu-id="c9c6e-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="c9c6e-105">UI 요소 목록</span><span class="sxs-lookup"><span data-stu-id="c9c6e-105">UI element list</span></span>  
 <span data-ttu-id="c9c6e-106">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="c9c6e-106">**Details**</span></span>  
 <span data-ttu-id="c9c6e-107">각 데이터 가져오기 작업에 대한 다음 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-107">Displays the following information for each data import operation.</span></span>  
  
|<span data-ttu-id="c9c6e-108">열</span><span class="sxs-lookup"><span data-stu-id="c9c6e-108">Column</span></span>|<span data-ttu-id="c9c6e-109">Description</span><span class="sxs-lookup"><span data-stu-id="c9c6e-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c9c6e-110">**작업 항목**</span><span class="sxs-lookup"><span data-stu-id="c9c6e-110">**Work Item**</span></span>|<span data-ttu-id="c9c6e-111">가져오고 있는 테이블 또는 뷰의 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-111">Displays the name of the table or view that is being imported.</span></span>|  
|<span data-ttu-id="c9c6e-112">**상태**</span><span class="sxs-lookup"><span data-stu-id="c9c6e-112">**Status**</span></span>|<span data-ttu-id="c9c6e-113">테이블 또는 뷰를 성공적으로 가져왔는지 여부와 가져온 행 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-113">Indicates whether the table or view was successfully imported and the number of rows that were imported.</span></span>|  
|<span data-ttu-id="c9c6e-114">**Message**</span><span class="sxs-lookup"><span data-stu-id="c9c6e-114">**Message**</span></span>|<span data-ttu-id="c9c6e-115">테이블 또는 뷰 가져오기에 실패한 경우 자세한 정보에 대한 링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-115">If the table or view import failed, displays a link to more information.</span></span> <span data-ttu-id="c9c6e-116">이 정보는 세부 정보 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-116">This information is displayed in the Details window.</span></span><br /><br /> <span data-ttu-id="c9c6e-117">테이블 또는 뷰 가져오기를 다시 시도하려면 마법사를 종료하고 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-117">To try again to import the table or view, exit the wizard and run it again.</span></span>|  
  
 <span data-ttu-id="c9c6e-118">**가져오기 중지**</span><span class="sxs-lookup"><span data-stu-id="c9c6e-118">**Stop Import**</span></span>  
 <span data-ttu-id="c9c6e-119">완료되기 전에 가져오기 작업을 중지하려면 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-119">Click to stop the import operation before it is finished.</span></span> <span data-ttu-id="c9c6e-120">이미 가져온 테이블 및 뷰는 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 디자이너에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-120">Tables and views that have already been imported will be displayed in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] designer.</span></span> <span data-ttu-id="c9c6e-121">아직 가져오지 않은 테이블 및 뷰는 가져오지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9c6e-121">Tables and views that have not been imported yet will not be imported.</span></span>  
  
  
