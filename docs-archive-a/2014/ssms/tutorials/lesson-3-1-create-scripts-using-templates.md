---
title: 템플릿을 사용하여 스크립트 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ed48014c-3fc9-48ff-8c0f-8d1822195f14
author: stevestein
ms.author: sstein
ms.openlocfilehash: b404ecc505e93c302e4c737f9c0b0161d9015519
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733408"
---
# <a name="create-scripts-using-templates"></a><span data-ttu-id="f4960-102">템플릿을 사용하여 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="f4960-102">Create Scripts Using Templates</span></span>
  <span data-ttu-id="f4960-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 에서는 많은 일반 태스크에 사용할 수 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 포함하는 스크립트 템플릿을 다수 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-103">Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides a large number of script templates containing the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for many common tasks.</span></span> <span data-ttu-id="f4960-104">이러한 템플릿에는 테이블 이름과 같이 사용자가 제공한 값에 대한 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-104">These templates contain parameters for the user-provided values such as a table name.</span></span> <span data-ttu-id="f4960-105">매개 변수를 사용하면 이름을 한 번 입력한 다음 스크립트 내에서 필요한 모든 위치에 자동으로 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-105">Using the parameters, you can type the name once and then automatically copy the name to all the necessary locations within the script.</span></span> <span data-ttu-id="f4960-106">사용자 지정 템플릿을 직접 작성하여 가장 자주 작성하는 스크립트를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-106">You can write your own custom templates to support the scripts that you write most often.</span></span> <span data-ttu-id="f4960-107">템플릿을 이동하거나 템플릿을 보관할 새 폴더를 만들어 템플릿 트리를 다시 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-107">You can also reorganize the template tree, moving templates or creating new folders to hold the templates.</span></span> <span data-ttu-id="f4960-108">다음 연습에서는 데이터 정렬 템플릿을 지정하여 템플릿으로 데이터베이스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-108">In the following practice, you will use a template to create a database, specifying collation template.</span></span>  
  
## <a name="using-templates"></a><span data-ttu-id="f4960-109">템플릿 사용</span><span class="sxs-lookup"><span data-stu-id="f4960-109">Using Templates</span></span>  
  
#### <a name="to-create-a-script-using-a-template"></a><span data-ttu-id="f4960-110">템플릿을 사용하여 스크립트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f4960-110">To create a script using a template</span></span>  
  
1.  <span data-ttu-id="f4960-111">[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 **보기** 메뉴에서 **템플릿 탐색기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-111">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], on the **View** menu, click **Template Explorer**.</span></span>  
  
2.  <span data-ttu-id="f4960-112">템플릿 탐색기에 있는 템플릿이 그룹으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-112">The templates in Template Explorer are organized into groups.</span></span> <span data-ttu-id="f4960-113">**데이터베이스**를 확장한 다음 **데이터베이스 만들기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-113">Expand **Database**, and then double-click **Create Database**.</span></span>  
  
3.  <span data-ttu-id="f4960-114">**데이터베이스 엔진에 연결** 대화 상자에서 연결 정보를 지정한 다음 **연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-114">In the **Connect to Database Engine** dialog box, complete the connection information and then click **Connect**.</span></span> <span data-ttu-id="f4960-115">**데이터베이스 만들기** 템플릿의 내용을 포함하는 새 쿼리 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-115">A new Query Editor window opens, containing the contents of the **Create Database** template.</span></span>  
  
4.  <span data-ttu-id="f4960-116">**쿼리** 메뉴에서 **템플릿 매개 변수 값 지정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-116">On the **Query** menu, click **Specify Values for Template Parameters**.</span></span>  
  
5.  <span data-ttu-id="f4960-117">**템플릿 매개 변수 값 지정** 대화 상자의 **값** 열에는 **Database_Name** 매개 변수에 대해 제안된 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-117">In the **Specify Values for Template Parameters** dialog box, the **Value** column contains a suggested value for the **Database_Name** parameter.</span></span> <span data-ttu-id="f4960-118">**Database Name** 매개 변수 상자에 **Marketing**을 입력한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-118">In the **Database Name** parameter box, type **Marketing**, and then click **OK**.</span></span> <span data-ttu-id="f4960-119">"Marketing"이 어떻게 스크립트의 여러 위치에 삽입되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f4960-119">Note how "Marketing" is inserted into the script in several locations.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="f4960-120">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="f4960-120">Next Task in Lesson</span></span>  
 [<span data-ttu-id="f4960-121">사용자 지정 템플릿 만들기</span><span class="sxs-lookup"><span data-stu-id="f4960-121">Create Custom Templates</span></span>](lesson-3-2-create-custom-templates.md)  
  
  
