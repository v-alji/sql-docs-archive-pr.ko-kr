---
title: 솔루션 탐색기에서 데이터 원본 삭제 (SSAS 다차원) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
author: minewiskan
ms.author: owend
ms.openlocfilehash: d6101c8704579894590994d88e0286197148b694
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660720"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a><span data-ttu-id="7ce0d-102">솔루션 탐색기에서 데이터 원본 삭제(SSAS 다차원)</span><span class="sxs-lookup"><span data-stu-id="7ce0d-102">Delete a Data Source in Solution Explorer (SSAS Multidimensional)</span></span>
  <span data-ttu-id="7ce0d-103">데이터 원본 개체를 삭제하여 Analysis Services 다차원 모델 프로젝트에서 해당 개체를 영구적으로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-103">You can delete a data source object to permanently remove it from an Analysis Services multidimensional model project.</span></span>  
  
 <span data-ttu-id="7ce0d-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 데이터 원본은 데이터 원본 뷰의 생성 기반을 제공하며 데이터 원본 뷰는 다시 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트나 데이터베이스의 차원, 큐브 및 마이닝 구조를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-104">In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], data sources provide the basis on which data source views are constructed, and data source views are in turn used to define dimensions, cubes, and mining structures in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="7ce0d-105">따라서 데이터 원본을 삭제하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 다른 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체가 무효화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-105">Therefore, deleting a data source may invalidate other [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="7ce0d-106">항상 개체를 삭제하기 전에 제공되는 종속 개체의 목록을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-106">You should always review the list of dependent objects that is provided before deleting the object.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7ce0d-107">다른 개체가 종속된 데이터 원본은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 온라인 모드로 열린 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 데이터베이스에서 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-107">Data sources on which other objects depend cannot be deleted from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database opened by [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in online mode.</span></span> <span data-ttu-id="7ce0d-108">데이터 원본을 삭제하기 전에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에서 해당 데이터 원본에 종속된 모든 개체를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-108">You must delete all objects in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database that depend on that data source before deleting the data source.</span></span> <span data-ttu-id="7ce0d-109">온라인 모드에 대한 자세한 내용은 [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-109">For more information about online mode, see [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md).</span></span>  
  
### <a name="to-delete-a-data-source"></a><span data-ttu-id="7ce0d-110">데이터 원본을 삭제하려면</span><span class="sxs-lookup"><span data-stu-id="7ce0d-110">To delete a data source</span></span>  
  
1.  <span data-ttu-id="7ce0d-111">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 데이터 원본을 삭제할 데이터베이스에 연결하거나 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-111">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project or connect to the database from which you want to delete a data source.</span></span>  
  
2.  <span data-ttu-id="7ce0d-112">**솔루션 탐색기**에서 **데이터 원본** 폴더를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-112">In **Solution Explorer**, expand the **Data Sources** folder.</span></span>  
  
3.  <span data-ttu-id="7ce0d-113">데이터 원본을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-113">Right-click the data source, and then click **Delete**.</span></span> <span data-ttu-id="7ce0d-114">**개체 삭제**  대화 상자가 나타나고, 데이터 원본을 삭제하는 경우 무효화될 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-114">The **Delete Objects**  dialog box appears, showing the objects that will be invalidated if you delete the data source.</span></span> <span data-ttu-id="7ce0d-115">**확인** 을 클릭하여 데이터 원본을 삭제하기 전에 이 목록을 신중하게 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-115">Review this list carefully before clicking **OK** to delete the data source.</span></span>  
  
4.  <span data-ttu-id="7ce0d-116">프로젝트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-116">Save the project.</span></span>  
  
     <span data-ttu-id="7ce0d-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트에서 데이터 원본을 삭제한 후 수정된 프로젝트를 저장해야 합니다. 그렇지 않으면 프로젝트에서 삭제된 데이터 원본을 로드할 때 삭제된 데이터 원본의 기본 XML 파일이 없으므로 다음에 프로젝트를 열 때 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7ce0d-117">After deleting a data source from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you must save the modified project or you will receive an error the next time you open the project because the underlying XML file for the deleted data source will be missing when the project attempts to load the deleted data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce0d-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7ce0d-118">See Also</span></span>  
 <span data-ttu-id="7ce0d-119">[다차원 모델의 데이터 원본](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="7ce0d-119">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="7ce0d-120">SSAS 다차원&#41;&#40;지원 되는 데이터 원본</span><span class="sxs-lookup"><span data-stu-id="7ce0d-120">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
