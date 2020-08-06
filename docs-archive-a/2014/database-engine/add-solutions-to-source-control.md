---
title: 소스 제어에 솔루션 추가 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- adding solutions
- solutions [SQL Server Management Studio], adding
ms.assetid: b9e36569-616d-4e47-9140-0978a9bfe923
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1c72949fd8257332a36af52ab287ed326eed5274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730896"
---
# <a name="add-solutions-to-source-control"></a><span data-ttu-id="ac5ec-102">원본 제어에 솔루션 추가</span><span class="sxs-lookup"><span data-stu-id="ac5ec-102">Add Solutions to Source Control</span></span>
  <span data-ttu-id="ac5ec-103">소스 제어에 솔루션을 추가할 경우 일반적으로 전체 솔루션과 솔루션에 포함된 모든 프로젝트를 추가하고 싶을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-103">When you add a solution to source control, you usually want to add the entire solution and all the projects it contains.</span></span> <span data-ttu-id="ac5ec-104">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]를 사용하여 솔루션을 원본 제어에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-104">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to add a solution to source control.</span></span>  
  
 <span data-ttu-id="ac5ec-105">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 프로젝트는 완전하게 로컬 디스크에 상주하므로</span><span class="sxs-lookup"><span data-stu-id="ac5ec-105">A [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] project resides completely on your local disk.</span></span> <span data-ttu-id="ac5ec-106">프로젝트를 로컬로 편집, 저장 및 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-106">You edit, save, and build projects locally.</span></span> <span data-ttu-id="ac5ec-107">프로젝트를 소스 제어에 추가한 후 **체크 아웃** 명령을 사용 하 여 프로젝트의 파일을 원본 제어에서 체크 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-107">After adding the project to source control, you can use the **Check Out** command to check the project's files out of source control.</span></span>  
  
### <a name="to-add-a-solution-to-source-control"></a><span data-ttu-id="ac5ec-108">원본 제어에 솔루션을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="ac5ec-108">To add a solution to source control</span></span>  
  
1.  <span data-ttu-id="ac5ec-109">솔루션 탐색기에서 추가할 솔루션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-109">In Solution Explorer, select the solution you want to add.</span></span>  
  
2.  <span data-ttu-id="ac5ec-110">**파일** 메뉴에서 **소스 제어**를 가리킨 다음 **원본 제어에 솔루션 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-110">On the **File** menu, point to **Source Control**, and then click **Add Solution to Source Control**.</span></span>  
  
3.  <span data-ttu-id="ac5ec-111">로그온하라는 메시지가 표시되면 원본 제어 공급자에 로그온합니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-111">If prompted, log on to your source control provider.</span></span>  
  
4.  <span data-ttu-id="ac5ec-112">**SourceSafe 프로젝트에 추가** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-112">The **Add to SourceSafe Project** dialog box appears.</span></span> <span data-ttu-id="ac5ec-113">프로젝트 이름이 **프로젝트** 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-113">The name of your project appears in the **Project** box.</span></span>  
  
5.  <span data-ttu-id="ac5ec-114">**폴더** 목록에서 프로젝트를 저장할 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-114">In the **Folders** list, open the folder where you want to place your project.</span></span> <span data-ttu-id="ac5ec-115">또는 **만들기** 를 클릭 하 여 **프로젝트** 상자에 이름이 표시 된 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac5ec-115">Alternatively, you can click **Create** to create a folder with the name displayed in the **Project** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5ec-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac5ec-116">See Also</span></span>  
 <span data-ttu-id="ac5ec-117">[소스 제어에 솔루션 및 프로젝트 추가](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span><span class="sxs-lookup"><span data-stu-id="ac5ec-117">[Add Solutions and Projects to Source Control](../../2014/database-engine/add-solutions-and-projects-to-source-control.md) </span></span>  
 [<span data-ttu-id="ac5ec-118">원본 제어에 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="ac5ec-118">Add Projects to Source Control</span></span>](../../2014/database-engine/add-projects-to-source-control.md)  
  
  
