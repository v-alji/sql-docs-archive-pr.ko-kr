---
title: '3단계: 플랫 파일 연결 관리자 수정 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b897f9412a8f2978ebe4137e3e79bf1d28c97844
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647111"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a><span data-ttu-id="8a18d-102">3단계: 플랫 파일 연결 관리자 수정</span><span class="sxs-lookup"><span data-stu-id="8a18d-102">Step 3: Modifying the Flat File Connection Manager</span></span>
  <span data-ttu-id="8a18d-103">이 태스크에서는 1단원에서 만들어 구성한 플랫 파일 연결 관리자를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-103">In this task, you will modify the Flat File connection manager that you created and configured in Lesson 1.</span></span> <span data-ttu-id="8a18d-104">처음 만든 플랫 파일 연결 관리자는 파일 하나를 정적으로 로드하도록 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-104">When originally created, the Flat File connection manager was configured to statically load a single file.</span></span> <span data-ttu-id="8a18d-105">플랫 파일 연결 관리자를 사용하여 반복적으로 파일을 로드하려면 런타임에 로드할 파일의 경로를 포함하는 사용자 정의 변수 `User:varFileName`을 허용하도록 연결 관리자의 ConnectionString 속성을 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-105">To enable the Flat File connection manager to iteratively load files, you must modify the ConnectionString property of the connection manager to accept the user-defined variable `User:varFileName`, which contains the path of the file to be loaded at run time.</span></span>  
  
 <span data-ttu-id="8a18d-106">사용자 정의 변수 `User::varFileName`의 값을 사용하도록 연결 관리자를 수정하여 해당 관리자의 ConnectionString 속성을 채우면 연결 관리자가 여러 플랫 파일에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-106">By modifying the connection manager to use the value of the user-defined variable, `User::varFileName`, to populate the ConnectionString property of the connection manager, the connection manager will be able to connect to different flat files.</span></span> <span data-ttu-id="8a18d-107">런타임에 Foreach 루프 컨테이너가 반복될 때마다 `User::varFileName` 변수가 동적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-107">At run time, each iteration of the Foreach Loop container will dynamically update the `User::varFileName` variable.</span></span> <span data-ttu-id="8a18d-108">따라서 변수를 업데이트하면 연결 관리자가 다른 플랫 파일에 연결하고 데이터 흐름 태스크가 다른 데이터 집합을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-108">Updating the variable, in turn, causes the connection manager to connect to a different flat file, and the data flow task to process a different set of data.</span></span>  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a><span data-ttu-id="8a18d-109">연결 문자열에 변수를 사용하도록 플랫 파일 연결 관리자를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="8a18d-109">To configure the Flat File connection manager to use a variable for the connection string</span></span>  
  
1.  <span data-ttu-id="8a18d-110">**연결 관리자** 창에서 **Sample Flat File Source Data**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-110">In the **Connection Managers** pane, right-click **Sample Flat File Source Data**, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="8a18d-111">속성 창에서 **식**에 대해 빈 셀을 클릭 한 다음 줄임표 단추 **(...)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-111">In the Properties window, for **Expressions**, click in the empty cell, and then click the ellipsis button **(...)**.</span></span>  
  
3.  <span data-ttu-id="8a18d-112">**속성 식 편집기** 대화 상자의 **속성** 열에서를 입력 하거나 선택 `ConnectionString` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-112">In the **Property Expressions Editor** dialog box, in the **Property** column, type or select `ConnectionString`.</span></span>  
  
4.  <span data-ttu-id="8a18d-113">**식** 열에서 줄임표 단추 **(...)** 를 클릭 하 여 **식 작성기** 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-113">In the **Expression** column, click the ellipsis button **(...)** to open the **Expression Builder** dialog box.</span></span>  
  
5.  <span data-ttu-id="8a18d-114">**식 작성기** 대화 상자에서 **변수** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-114">In the **Expression Builder** dialog box, expand the **Variables** node.</span></span>  
  
6.  <span data-ttu-id="8a18d-115">**사용자:: varFileName**변수를 **식** 상자로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-115">Drag the variable, **User::varFileName**, into the **Expression** box.</span></span>  
  
7.  <span data-ttu-id="8a18d-116">**확인** 을 클릭하여 **식 작성기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-116">Click **OK** to close the **Expression Builder** dialog box.</span></span>  
  
8.  <span data-ttu-id="8a18d-117">다시 **확인** 을 클릭하여 **PropertiesExpressionEditor** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8a18d-117">Click **OK** again to close the **Property Expressions Editor** dialog box.</span></span>  
  
## <a name="next-lesson-task"></a><span data-ttu-id="8a18d-118">다음 단원 태스크</span><span class="sxs-lookup"><span data-stu-id="8a18d-118">Next Lesson Task</span></span>  
 [<span data-ttu-id="8a18d-119">4단계: 2단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="8a18d-119">Step 4: Testing the Lesson 2 Tutorial Package</span></span>](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  
