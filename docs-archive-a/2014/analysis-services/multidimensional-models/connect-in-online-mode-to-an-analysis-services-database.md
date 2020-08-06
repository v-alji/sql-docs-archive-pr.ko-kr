---
title: 온라인 모드에서 Analysis Services 데이터베이스에 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 363beb7132eae92907198979fe2d9892c5d07b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737102"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a><span data-ttu-id="b7711-102">온라인 모드로 Analysis Services 데이터베이스에 연결</span><span class="sxs-lookup"><span data-stu-id="b7711-102">Connect in Online Mode to an Analysis Services Database</span></span>
  <span data-ttu-id="b7711-103">기존 데이터베이스에 직접 연결 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 해당 데이터베이스 내의 개체를 직접 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-103">You can connect directly to an existing [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and directly modify objects within that database.</span></span> <span data-ttu-id="b7711-104">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스에 직접 연결하면 개체 변경이 즉시 수행되며 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 내에 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]프로젝트가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-104">When you connect directly to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database, changes to objects occur immediately and no [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project is created within [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a><span data-ttu-id="b7711-105">SQL Server Data Tools를 사용하여 Analysis Services 데이터베이스에 직접 연결하려면</span><span class="sxs-lookup"><span data-stu-id="b7711-105">To Connect Directly to an Analysis Services Database by using SQL Server Data Tools</span></span>  
  
1.  <span data-ttu-id="b7711-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-106">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="b7711-107">**파일** 메뉴에서 **열기** 를 가리킨 다음 **Analysis Services 데이터베이스**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-107">On the **File** menu, point to **Open** and then click **Analysis Services Database**.</span></span>  
  
3.  <span data-ttu-id="b7711-108">**기존 데이터베이스에 연결**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-108">Select **Connect to existing database**.</span></span>  
  
4.  <span data-ttu-id="b7711-109">서버 이름과 데이터베이스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-109">Specify the server name and the database name.</span></span>  
  
     <span data-ttu-id="b7711-110">데이터베이스 이름을 입력하거나 서버를 쿼리하여 서버의 기존 데이터베이스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-110">You can either type the database name or query the server to view the existing databases on the server.</span></span>  
  
5.  <span data-ttu-id="b7711-111">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-111">Click **OK**.</span></span>  
  
     <span data-ttu-id="b7711-112">이제 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스 내의 모든 개체를 직접 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7711-112">You can now directly edit any objects within the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7711-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7711-113">See Also</span></span>  
 <span data-ttu-id="b7711-114">[개발 단계 중 Analysis Services 프로젝트 및 데이터베이스 작업](work-with-analysis-services-projects-and-databases-in-development.md) </span><span class="sxs-lookup"><span data-stu-id="b7711-114">[Working with Analysis Services Projects and Databases During the Development Phase](work-with-analysis-services-projects-and-databases-in-development.md) </span></span>  
 [<span data-ttu-id="b7711-115">SSDT&#40;SQL Server Data Tools&#41;를 사용하여 다차원 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="b7711-115">Creating Multidimensional Models Using SQL Server Data Tools &#40;SSDT&#41;</span></span>](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  
