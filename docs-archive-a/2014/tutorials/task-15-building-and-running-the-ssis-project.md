---
title: '작업 15: SSIS 프로젝트 빌드 및 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 13adf4e0-216a-4992-b13d-b7b1e1629e77
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 2a008cd848c95b48e6e22798b6ef903942b4d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734659"
---
# <a name="task-15-building-and-running-the-ssis-project"></a><span data-ttu-id="e3cc1-102">태스크 15: SSIS 프로젝트 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="e3cc1-102">Task 15: Building and Running the SSIS Project</span></span>

  <span data-ttu-id="e3cc1-103">이 작업에서는 SSIS 프로젝트를 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-103">In this task, you build and run the SSIS project.</span></span> <span data-ttu-id="e3cc1-104">64 비트 버전의 Excel 2010이 컴퓨터에 설치 되어 있는 경우 Excel 원본이 작동 하려면 **Run64BitRuntime** 값을 **False** 로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-104">If you have the 64-bit version of Excel 2010 installed on your computer, you should set the value of **Run64BitRuntime** to **False** for the Excel source to work.</span></span>  
  
1.  <span data-ttu-id="e3cc1-105">**솔루션 탐색기** 창의 메뉴에서 **프로젝트** 를 클릭 하 고 **CleanseAndCurateSuppliers 속성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-105">In the **Solution Explorer** window, click **Project** on the menu, and click **CleanseAndCurateSuppliers Properties**.</span></span>  
  
2.  <span data-ttu-id="e3cc1-106">**속성** 대화 상자에서 왼쪽의 **구성 속성** 을 확장 하 고 **디버깅**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-106">In the **Properties** dialog box, expand **Configuration Properties** on left, and click **Debugging**.</span></span>  
  
3.  <span data-ttu-id="e3cc1-107">**Run64BitRuntime** 을 **False**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-107">Set **Run64BitRuntime** to **False**.</span></span>  
  
     <span data-ttu-id="e3cc1-108">![CleanseAndCurateSuppliers 프로젝트 속성](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers 프로젝트 속성")</span><span class="sxs-lookup"><span data-stu-id="e3cc1-108">![CleanseAndCurateSuppliers Project Properties](../../2014/tutorials/media/et-buildingandrunningthessisproject-01.jpg "CleanseAndCurateSuppliers Project Properties")</span></span>  
  
4.  <span data-ttu-id="e3cc1-109">**확인**을 클릭하여 **속성** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-109">Click **OK** to close the **Properties** dialog box.</span></span>  
  
5.  <span data-ttu-id="e3cc1-110">메뉴 모음에서 **빌드** 를 클릭 하 고 **CleanseAndCurateSuppliers 빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-110">Click **Build** on menu bar and click **Build CleanseAndCurateSuppliers**.</span></span> <span data-ttu-id="e3cc1-111">빌드 오류가 없는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-111">Make sure that there are no build errors.</span></span>  
  
6.  <span data-ttu-id="e3cc1-112">메뉴 모음에서 **디버그** 를 클릭 하 고 **디버깅 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-112">Click **Debug** on the menu bar and click **Start Debugging**.</span></span>  
  
7.  <span data-ttu-id="e3cc1-113">**진행률** 창에서 메시지를 검토 하 고 패키지를 실행 하 고 성공적으로 종료 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-113">Review messages in the **Progress** window and verify that package executed and ended successfully.</span></span>  
  
     <span data-ttu-id="e3cc1-114">![진행률 창의 결과](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "진행률 창의 결과")</span><span class="sxs-lookup"><span data-stu-id="e3cc1-114">![Results from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-02.jpg "Results from Progress Window")</span></span>  
  
     <span data-ttu-id="e3cc1-115">![진행률 창의 마지막 상태](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "진행률 창의 마지막 상태")</span><span class="sxs-lookup"><span data-stu-id="e3cc1-115">![Final Status from Progress Window](../../2014/tutorials/media/et-buildingandrunningthessisproject-03.jpg "Final Status from Progress Window")</span></span>  
  
8.  <span data-ttu-id="e3cc1-116">메뉴 모음에서 **디버그** 를 클릭 하 고 디버깅 **중지** 를 클릭 하 여 디버깅 세션을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-116">Click **Debug** on menu bar and click **Stop Debugging** to stop the debugging session.</span></span> <span data-ttu-id="e3cc1-117">패키지가 실패하면 데이터 뷰어를 사용하도록 설정하고 구성 요소 간 데이터 흐름 방식을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3cc1-117">If the package fails, you should enable data viewers and see how the data flows between components.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="e3cc1-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e3cc1-118">Next Step</span></span>  
 [<span data-ttu-id="e3cc1-119">태스크 16: 마스터 데이터 관리자에서 확인</span><span class="sxs-lookup"><span data-stu-id="e3cc1-119">Task 16: Verifying with Master Data Manager</span></span>](../../2014/tutorials/task-16-verifying-with-master-data-manager.md)  
  
  
