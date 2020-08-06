---
title: 데이터 마이닝 뷰어에서 사용 되는 색 변경 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- VS.TOOLSOPTIONSPAGES.BUSINESS_INTELLIGENCE_DESIGNERS.ANALYSIS_SERVICES_DESIGNERS.DATA_MINING_VIEWERS
ms.assetid: 9de2fc2a-fca5-456b-b2bd-13586e7951e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8abee369a99bb2fa7d0590ca85d87c1bda76ba2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661439"
---
# <a name="change-the-colors-used-in-the-data-mining-viewer"></a><span data-ttu-id="c7b27-102">데이터 마이닝 뷰어에서 사용되는 색 변경</span><span class="sxs-lookup"><span data-stu-id="c7b27-102">Change the Colors Used in the Data Mining Viewer</span></span>
  <span data-ttu-id="c7b27-103">데이터 마이닝 뷰어에서 데이터 계열, 노드 또는 클러스터를 표시하는 데 사용되는 색을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-103">You can change the colors that are used in the data mining viewers to display data series, nodes, or clusters.</span></span> <span data-ttu-id="c7b27-104">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 옵션을 설정하여 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-104">You do this by setting options in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="c7b27-105">설정을 변경한 후에는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 사용하여 보는 모든 모델에 색 선택이 적용되지만 새 색을 보기 위해서는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 를 닫고 뷰어에서 모델을 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-105">After you have changed the settings, the color selections apply to all models that you view by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]; however, you must close [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and reopen the model in the viewer to see the new colors.</span></span>  
  
### <a name="to-change-the-colors-used-in-the-data-mining-viewers"></a><span data-ttu-id="c7b27-106">데이터 마이닝 뷰어에서 사용되는 색을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="c7b27-106">To change the colors used in the data mining viewers</span></span>  
  
1.  <span data-ttu-id="c7b27-107">**또는** 의 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 도구 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]메뉴에서 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-107">On the **Tools** menu of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], select **Options**.</span></span>  
  
2.  <span data-ttu-id="c7b27-108">**옵션** 대화 상자에서 **디자이너**를 확장한 다음 **데이터 마이닝 뷰어**를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-108">In the **Options** dialog box, expand **Designers**, and then expand **Data Mining Viewers**.</span></span>  
  
3.  <span data-ttu-id="c7b27-109">변경할 뷰어 속성을 찾고 현재 색 선택을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-109">Find the viewer property that you want to change, and click the current color selection.</span></span>  
  
4.  <span data-ttu-id="c7b27-110">드롭다운 목록에서 새 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-110">Select a new color from the dropdown list.</span></span> <span data-ttu-id="c7b27-111">**사용자 지정** 탭을 클릭하여 현재 컴퓨터에서 사용할 수 있는 사용자 지정 색의 팔레트에서 색을 선택하거나 **시스템** 을 클릭하여 Windows 색 구성표에 지정된 색 중에서 색을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-111">Click the **Custom** tab to select a color from the palette of custom colors available on the current computer, or click **System** to select a color from among the colors specified in the Windows color scheme.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7b27-112">사용자 지정 색을 사용하는 경우 색은 색 아이콘 및 색의 RBG 값으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-112">If you use a custom color, the color is represented by a color icon and the RBG values of the color.</span></span> <span data-ttu-id="c7b27-113">시스템 색 또는 웹 색을 사용하는 경우 색은 색 아이콘 및 색 이름으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c7b27-113">If you use a System color or Web color, the color is represented by a color icon and the name of the color.</span></span>  
  
  
