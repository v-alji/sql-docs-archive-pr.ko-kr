---
title: 셀 내 항목 변경(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 80ef171713e6505867e00e343ce17b70cab9045a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742836"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a><span data-ttu-id="e5f71-102">셀 내 항목 변경(보고서 작성기 및 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e5f71-102">Change an Item Within a Cell (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e5f71-103">입력란, 선 또는 이미지와 같은 비컨테이너 항목만 새 보고서 항목으로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-103">Only a non-container item, such as a text box, line, or image, can be replaced by a new report item.</span></span> <span data-ttu-id="e5f71-104">예를 들어 테이블을 입력란으로 끌어 테이블로 입력란을 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-104">For example, you can drag a table into a text box to replace the text box with a table.</span></span>  
  
 <span data-ttu-id="e5f71-105">셀에 사각형, 목록, 테이블, 행렬 등과 같은 컨테이너 항목이 포함되어 있는 경우 새 항목은 포함 항목을 대체하지 않고 항목에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-105">If the cell contains a container item such as a rectangle, list, table, or matrix, the new item is added to the containing item instead of replacing it.</span></span> <span data-ttu-id="e5f71-106">컨테이너 항목을 새 항목으로 대체하려면 컨테이너를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-106">To replace a container item with a new item, delete the container.</span></span> <span data-ttu-id="e5f71-107">컨테이너 항목을 삭제하면 다른 항목으로 대체할 수 있는 입력란으로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-107">Deleting the container item replaces it with a text box, which you can then replace with another item.</span></span>  
  
 <span data-ttu-id="e5f71-108">기본적으로 테이블, 행렬 또는 목록 데이터 영역의 모든 셀에는 입력란이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-108">By default, all cells in a table, matrix, or list data region contain a text box.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a><span data-ttu-id="e5f71-109">셀에서 항목을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="e5f71-109">To change an item within a cell</span></span>  
  
-   <span data-ttu-id="e5f71-110">**삽입** 탭의 **데이터 영역** 또는 **보고서 항목** 그룹에서 보고서에 추가할 항목을 클릭한 다음 보고서를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-110">On the **Insert** tab, in the **Data Regions** or **Report Items** group, click the item that you want to add to the report, and then click the report.</span></span> <span data-ttu-id="e5f71-111">보고서에 항목이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-111">The item is added to the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e5f71-112">이미지 보고서 항목을 끌어서 셀에 놓으면 **이미지 속성** 대화 상자가 열립니다. 이 대화 상자에서 이미지를 셀에 추가하기 전에 이미지 원본 등의 속성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5f71-112">The **Image Properties** dialog box opens when you drag an image report item to a cell, where you can set properties such as the source of the image before the image is added to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5f71-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5f71-113">See Also</span></span>  
 <span data-ttu-id="e5f71-114">[이미지, 입력란, 사각형 및 선&#40;보고서 작성기 및 SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e5f71-114">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e5f71-115">목록&#40;보고서 작성기 및 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e5f71-115">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
