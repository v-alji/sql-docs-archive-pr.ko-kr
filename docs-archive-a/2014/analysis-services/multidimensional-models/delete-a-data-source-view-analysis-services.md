---
title: 데이터 원본 뷰 삭제 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
author: minewiskan
ms.author: owend
ms.openlocfilehash: 24b587e8d8961161ea803915c31d117c11f7cf2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660717"
---
# <a name="delete-a-data-source-view-analysis-services"></a><span data-ttu-id="a3a26-102">데이터 원본 뷰 삭제(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a3a26-102">Delete a Data Source View (Analysis Services)</span></span>
  <span data-ttu-id="a3a26-103">OLAP 프로젝트에서 DSV(데이터 원본 뷰)를 더 이상 사용하지 않으려는 경우 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]의 프로젝트에서 해당 뷰를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-103">If you are no longer using a data source view (DSV) in an OLAP project, you can delete it from the project in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a3a26-104">DSV 삭제는 영구적입니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-104">Deleting a DSV is permanent.</span></span> <span data-ttu-id="a3a26-105">삭제한 DSV는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-105">You cannot restore a deleted DSV to a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="a3a26-106">다른 개체가 종속된 DSV는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 온라인 모드로 열린 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 데이터베이스에서 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-106">DSVs that other objects depend on cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="a3a26-107">서버에서 실행하는 데이터베이스에 연결된 프로젝트에서 DSV를 삭제하려면 DSV 자체를 삭제하기 전에 먼저 해당 DSV에 종속된 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 개체를 모두 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-107">To delete a DSV from a project that is connected o a database running on a server, you must first delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that DSV before deleting the DSV itself.</span></span>  
  
 <span data-ttu-id="a3a26-108">DSV를 삭제하면 이 뷰에 종속된 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체도 무효화되므로 DSV를 삭제하기 전에 DSV를 제거할 경우 무효화될 개체 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-108">Deleting a DSV will invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects that depend on it, so before you delete the DSV, you will see the list of objects that will become invalid once the DSV is removed.</span></span> <span data-ttu-id="a3a26-109">이 목록을 신중하게 검토하여 계속 사용할 개체가 목록에 포함되지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a3a26-109">Review this list carefully to be sure that it does not include objects you still expect to use.</span></span>  
  
 <span data-ttu-id="a3a26-110">![개체 삭제 대화 상자](../media/ssas-olapdsv-deleteobjects.gif "개체 삭제 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="a3a26-110">![Delete Objects dialog box](../media/ssas-olapdsv-deleteobjects.gif "Delete Objects dialog box")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a26-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a3a26-111">See Also</span></span>  
 <span data-ttu-id="a3a26-112">[다차원 모델의 데이터 원본 뷰](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="a3a26-112">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="a3a26-113">데이터 원본 뷰에서 속성 변경&#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="a3a26-113">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
  
