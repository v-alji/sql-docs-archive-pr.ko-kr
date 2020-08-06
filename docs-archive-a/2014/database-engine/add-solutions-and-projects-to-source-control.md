---
title: 소스 제어에 솔루션 및 프로젝트 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], source controls
- solutions [SQL Server Management Studio], source controls
- source controls [SQL Server Management Studio], solutions
- source controls [SQL Server Management Studio], projects
ms.assetid: 3eaed80e-6f55-42ea-a964-aca31c09d055
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5256795677f4e8ce4249737d25d3ded1c4cd69c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730911"
---
# <a name="add-solutions-and-projects-to-source-control"></a><span data-ttu-id="a7e2b-102">원본 제어에 솔루션 및 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="a7e2b-102">Add Solutions and Projects to Source Control</span></span>
  <span data-ttu-id="a7e2b-103">솔루션을 원본 제어에 추가할 경우 솔루션은 원본 제어 공급자가 작성 및 유지 관리하는 동적 버전 관리 보관의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-103">When you add a solution to source control, the solution becomes part of a dynamic versioning archive created and maintained by the source control provider.</span></span> <span data-ttu-id="a7e2b-104">누군가가 솔루션의 새 버전을 체크 인할 때마다 해당 버전은 보관의 일부가 되며 다른 소스 제어 사용자가 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-104">Each time someone checks in a new version of the solution, that version becomes part of the archive and is available to other source control users.</span></span>  
  
 <span data-ttu-id="a7e2b-105">또한 솔루션을 소스 제어에 추가하면 중앙 집중화된 파일 관리 시스템이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-105">Adding a solution to source control also starts a system of centralized file management.</span></span> <span data-ttu-id="a7e2b-106">[!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe와 같은 소스 제어 공급자는 소스 제어 항목에 대한 액세스를 제어합니다. 따라서 소스 제어 클라이언트는 체크 아웃을 하지 않은 상태에서 소스 제어 파일의 로컬 복사본에 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-106">Source control providers, such as [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe, control access to source-controlled items; source control clients cannot write to local copies of source-controlled files without checking them out.</span></span>  
  
 <span data-ttu-id="a7e2b-107">다음 표에서는 이 섹션에서 다루는 항목에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-107">The following table describes the topics in this section.</span></span>  
  
|<span data-ttu-id="a7e2b-108">항목</span><span class="sxs-lookup"><span data-stu-id="a7e2b-108">Topic</span></span>|<span data-ttu-id="a7e2b-109">Description</span><span class="sxs-lookup"><span data-stu-id="a7e2b-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a7e2b-110">원본 제어에 솔루션 추가</span><span class="sxs-lookup"><span data-stu-id="a7e2b-110">Add Solutions to Source Control</span></span>](../../2014/database-engine/add-solutions-to-source-control.md)|<span data-ttu-id="a7e2b-111">추가할 수 있는 프로젝트 형식을 설명하고 솔루션을 소스 제어에 추가하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-111">Describes the project types you can add, and provides instructions on how to add a solution to source control.</span></span>|  
|[<span data-ttu-id="a7e2b-112">원본 제어에 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="a7e2b-112">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)|<span data-ttu-id="a7e2b-113">프로젝트를 솔루션에 추가하는 방법에 대한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a7e2b-113">Provides instructions on how to add a project to a solution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7e2b-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7e2b-114">See Also</span></span>  
 [<span data-ttu-id="a7e2b-115">원본 제어에서 솔루션 및 프로젝트 열기</span><span class="sxs-lookup"><span data-stu-id="a7e2b-115">Open Solutions and Projects from Source Control</span></span>](../../2014/database-engine/open-solutions-and-projects-from-source-control.md)  
  
  
