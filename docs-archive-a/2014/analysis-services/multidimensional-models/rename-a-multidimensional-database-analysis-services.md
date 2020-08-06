---
title: 다차원 데이터베이스 이름 바꾸기 (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- renaming databases
ms.assetid: 15fdaec7-f3e4-44d9-9b78-1a1d78c484e0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3974e7671aff5d1cba22b10563bbc85a129a1dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652401"
---
# <a name="rename-a-multidimensional-database-analysis-services"></a><span data-ttu-id="82159-102">다차원 데이터베이스 이름 바꾸기(Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="82159-102">Rename a Multidimensional Database (Analysis Services)</span></span>
  <span data-ttu-id="82159-103">데이터베이스의 이름을 변경 하는 방식은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 연결 하는 방법에 따라 달라 집니다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="82159-103">The manner in which you change the name of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database depends upon how you connect to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="82159-104">기존 데이터베이스의 이름을 변경하려면 온라인 모드로 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-104">To change the name of an existing database, you must connect in online mode.</span></span> <span data-ttu-id="82159-105">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트의 개체를 인스턴스화할 데이터베이스의 이름을 변경하려면 프로젝트 모드에서 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-105">To change the name of the database into which objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project will be instantiated, you must connect in project mode.</span></span>  
  
### <a name="to-change-the-database-name-in-online-mode"></a><span data-ttu-id="82159-106">온라인 모드에서 데이터베이스 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="82159-106">To change the database name in online mode</span></span>  
  
1.  <span data-ttu-id="82159-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 사용하여 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 직접 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-107">Using [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], connect directly to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="82159-108">솔루션 탐색기에서 데이터베이스를 마우스 오른쪽 단추로 클릭한 다음 **데이터베이스 편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-108">In Solution Explorer, right-click the database and then click **Edit Database**.</span></span>  
  
3.  <span data-ttu-id="82159-109">**데이터베이스 이름** 입력란에서 데이터베이스 이름을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-109">In the **Database name** text box, change the database name.</span></span>  
  
4.  <span data-ttu-id="82159-110">도구 모음에서 **저장** 또는 **모두 저장** 을 클릭하거나 **파일** 메뉴에서 **선택한 항목 저장** 또는 **모두 저장** 을 클릭하거나 **데이터베이스 디자이너** 를 닫고 메시지가 표시되면 **저장** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-110">Click **Save** or **Save All** on the toolbar, click **Save Selected Items** or **Save All** on the **File** menu, or close the **Database Designer** and then click **Save** when prompted.</span></span>  
  
     <span data-ttu-id="82159-111">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 데이터베이스 이름이 업데이트되고 솔루션 탐색기의 데이터베이스 개체가 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="82159-111">The database name is updated in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and the database object in Solution Explorer is refreshed.</span></span>  
  
### <a name="to-change-the-database-name-in-project-mode"></a><span data-ttu-id="82159-112">프로젝트 모드에서 데이터베이스 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="82159-112">To change the database name in project mode</span></span>  
  
1.  <span data-ttu-id="82159-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82159-113">Open the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="82159-114">솔루션 탐색기에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-114">In Solution Explorer, right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="82159-115">**속성 페이지** 대화 상자의 **구성 속성** 섹션에서 **배포** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-115">In the **Property Pages** dialog box, click **Deployment** in the **Configuration Properties** section.</span></span>  
  
4.  <span data-ttu-id="82159-116">**데이터베이스** 속성을 새 데이터베이스 이름으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-116">Change the **Database** property to the new database name.</span></span>  
  
     <span data-ttu-id="82159-117">다음에 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로젝트를 배포하면 새 데이터베이스 이름으로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="82159-117">The next time the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is deployed, it will be deployed to this new database name.</span></span> <span data-ttu-id="82159-118">이 데이터베이스가 이미 있으면 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="82159-118">If this database already exists, it will be overwritten.</span></span>  
  
### <a name="to-change-the-database-name-using-sql-server-management-studio"></a><span data-ttu-id="82159-119">SQL Server Management Studio를 사용하여 데이터베이스 이름을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="82159-119">To change the database name using SQL Server Management Studio</span></span>  
  
-   <span data-ttu-id="82159-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 마우스 오른쪽 단추로 클릭하고 Name 속성을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="82159-120">Right-click the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and edit the Name property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82159-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82159-121">See Also</span></span>  
 <span data-ttu-id="82159-122">[Analysis Services에서 서버 속성 구성](../server-properties/server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="82159-122">[Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) </span></span>  
 <span data-ttu-id="82159-123">[다차원 데이터베이스 속성 &#40;Analysis Services&#41;설정](set-multidimensional-database-properties-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="82159-123">[Set Multidimensional Database Properties &#40;Analysis Services&#41;](set-multidimensional-database-properties-analysis-services.md) </span></span>  
 <span data-ttu-id="82159-124">[SSDT&#41;&#40;Analysis Services 프로젝트 속성 구성](configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="82159-124">[Configure Analysis Services Project Properties &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md) </span></span>  
 [<span data-ttu-id="82159-125">Analysis Services 프로젝트 배포&#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="82159-125">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](deploy-analysis-services-projects-ssdt.md)  
  
  
