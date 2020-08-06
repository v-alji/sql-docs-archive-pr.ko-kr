---
title: '1 단원: 웹 서비스 클라이언트 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0070daa6-56b0-4663-83b2-44c96acafad8
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: eda9413867c4ca6d44a5cf98b82be9bddc04d0f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734711"
---
# <a name="lesson-1-creating-the-web-service-client-project"></a><span data-ttu-id="ae271-102">1단원: Web Service 클라이언트 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="ae271-102">Lesson 1: Creating the Web Service Client Project</span></span>
  <span data-ttu-id="ae271-103">이 연습에서는</span><span class="sxs-lookup"><span data-stu-id="ae271-103">For this walkthrough, you will create a simple console application that accesses the Report Server Web service.</span></span> <span data-ttu-id="ae271-104">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 개발 환경을 사용하여 보고서 서버 웹 서비스에 액세스하는 간단한 콘솔 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-104">This walkthrough assumes you are developing in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
### <a name="to-create-a-console-application"></a><span data-ttu-id="ae271-105">콘솔 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="ae271-105">To create a console application</span></span>  
  
1.  <span data-ttu-id="ae271-106">**파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트** 를 클릭하여 **새 프로젝트** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-106">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="ae271-107">왼쪽 창의 **설치된 템플릿**아래에서 **Visual Basic** 또는 **Visual C#** 노드를 클릭한 다음 확장된 목록에서 프로젝트 형식의 범주를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-107">In the left pane, under **Installed Templates**, click either **Visual Basic** or the **Visual C#** node, and select a category of project types from the expanded list.</span></span>  
  
3.  <span data-ttu-id="ae271-108">**콘솔 애플리케이션** 프로젝트 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-108">Choose the **Console Application** project type.</span></span>  
  
4.  <span data-ttu-id="ae271-109">**이름** 입력란에 프로젝트 이름을</span><span class="sxs-lookup"><span data-stu-id="ae271-109">In the **Name** box, enter a name for your project.</span></span> <span data-ttu-id="ae271-110">이름을 입력 `GetPropertiesSample` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-110">Type the name `GetPropertiesSample`.</span></span>  
  
5.  <span data-ttu-id="ae271-111">**위치** 상자에 프로젝트를 저장할 경로를 입력 하거나 **찾아보기** 를 클릭 하 여 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-111">In the **Location** box, enter the path where you want to save your project, or click **Browse** to navigate to the folder.</span></span>  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]<span data-ttu-id="ae271-112">프로젝트의 축소 된 보기가 솔루션 탐색기 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-112">A collapsed view of your project appears in Solution Explorer.</span></span>  
  
     <span data-ttu-id="ae271-113">솔루션 탐색기에서 프로젝트 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-113">In Solution Explorer, expand the project node.</span></span> <span data-ttu-id="ae271-114">기본 이름이 Program.cs (의 경우 module1.vb) 인 파일이 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 프로젝트에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ae271-114">A file with the default name of Program.cs (Module1.vb for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) has been added to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae271-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae271-115">See Also</span></span>  
 <span data-ttu-id="ae271-116">[2 단원: 웹 참조 추가](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ae271-116">[Lesson 2: Adding a Web Reference](../../2014/tutorials/lesson-2-adding-a-web-reference.md) </span></span>  
 [<span data-ttu-id="ae271-117">Visual Basic 또는 Visual C&#35; &#40;SSRS 자습서를 사용 하 여 보고서 서버 웹 서비스에 액세스&#41;</span><span class="sxs-lookup"><span data-stu-id="ae271-117">Accessing the Report Server Web Service Using Visual Basic or Visual C&#35; &#40;SSRS Tutorial&#41;</span></span>](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
