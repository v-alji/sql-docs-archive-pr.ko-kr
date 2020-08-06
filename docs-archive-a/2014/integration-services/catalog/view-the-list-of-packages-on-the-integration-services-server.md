---
title: Integration Services 서버의 패키지 목록 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47b30f9ea0b2abae73f9260b873b7c8436c423eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87727315"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a><span data-ttu-id="e0964-102">Integration Services 서버의 패키지 목록 보기</span><span class="sxs-lookup"><span data-stu-id="e0964-102">View the List of Packages on the Integration Services Server</span></span>
  <span data-ttu-id="e0964-103">다음 두 가지 방법 중 하나를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 저장된 패키지 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-103">You can view the list of packages that are stored on the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server in one of two ways.</span></span>  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="e0964-104">액세스</span><span class="sxs-lookup"><span data-stu-id="e0964-104">access</span></span>  
 <span data-ttu-id="e0964-105">서버에 저장된 패키지 목록을 보려면 [catalog.packages&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database) 뷰를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-105">To view the list of packages that are stored on the server, query the view, [catalog.packages &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database).</span></span>  
  
 <span data-ttu-id="e0964-106">위치: [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0964-106">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
 <span data-ttu-id="e0964-107">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 사용하여 서버에 저장된 패키지를 보려면 아래 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-107">To view packages stored on the server by using Object Explorer in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], follow the procedure below.</span></span>  
  
### <a name="to-view-packages-using-ssmanstudiofull"></a><span data-ttu-id="e0964-108">다음을 사용하여 패키지를 보려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0964-108">To view packages using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]</span></span>  
  
1.  <span data-ttu-id="e0964-109">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-109">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connect to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="e0964-110">즉, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-110">That is, connect to the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] that hosts the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] database.</span></span>  
  
2.  <span data-ttu-id="e0964-111">개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-111">In Object Explorer, expand the tree to display the **Integration Services Catalogs** node.</span></span>  
  
3.  <span data-ttu-id="e0964-112">**Integration Services 카탈로그** 노드를 확장하여 **SSISDB** 노드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-112">Expand the **Integration Services Catalogs** node to display the **SSISDB** node.</span></span>  
  
4.  <span data-ttu-id="e0964-113">**SSISDB** 노드를 확장하여 하나 이상의 폴더 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-113">Expand the **SSISDB** node to display a list of one or more folders.</span></span> <span data-ttu-id="e0964-114">각 폴더에는 **프로젝트** 폴더에 있는 하나 이상의 프로젝트가 포함되며 각 프로젝트에는 **패키지** 폴더의 패키지가 하나 이상 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0964-114">Each folder contains one or more projects in the **Projects** folder, and each project contains one more packages in the **Packages** folder.</span></span>  
  
  
