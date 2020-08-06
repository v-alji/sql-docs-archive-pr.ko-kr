---
title: '작업 4: SQL Server Data Tools을 사용 하 여 SSIS 프로젝트 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 07976dbd2c84b1385d79ce3f4ce4f616e0f706b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87733343"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a><span data-ttu-id="b406f-102">태스크 4: SQL Server Data Tools를 사용하여 SSIS 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="b406f-102">Task 4: Creating an SSIS Project using SQL Server Data Tools</span></span>
  <span data-ttu-id="b406f-103">이 작업에서는 공급자 데이터 정리 및 일치를 자동화하기 위해 **SQL Server Data Tools** 를 사용해서 SSIS 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-103">In this task, you create an SSIS project by using **SQL Server Data Tools** to automate cleansing and matching supplier data.</span></span>

1.  <span data-ttu-id="b406f-104">**SQL Server Data Tools**를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-104">Launch **SQL Server Data Tools**.</span></span> <span data-ttu-id="b406f-105">시작을 클릭하고, **모든 프로그램**을 가리킨 후 **Microsoft SQL Server 2012**를 확장하고 **SQL Server Data Tools**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-105">Click Start, point to **All Programs**, expand **Microsoft SQL Server 2012**, and click **SQL Server Data Tools**.</span></span>

2.  <span data-ttu-id="b406f-106">**파일** 메뉴에서 **새로 만들기**를 가리키고 **프로젝트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-106">On the **File** menu, point to **New**, and click **Project**.</span></span>

3.  <span data-ttu-id="b406f-107">**설치된 템플릿** 창에서 **비즈니스 인텔리전스** 를 확장하고 **Integration Services**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-107">Expand **Business Intelligence** in the **Installed Templates** pane, and select **Integration Services**.</span></span>

     <span data-ttu-id="b406f-108">![Visual Studio - 새 프로젝트 대화 상자](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - 새 프로젝트 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="b406f-108">![Visual Studio - New Project Dialog Box](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - New Project Dialog Box")</span></span>

4.  <span data-ttu-id="b406f-109">**프로젝트 형식 목록** 에서 **Integration Services 프로젝트**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-109">Select **Integration Services Project** in the **list of project types**.</span></span>

5.  <span data-ttu-id="b406f-110">**이름** 에 **CleanseAndCurateSuppliers** 를 입력하고 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-110">Type **CleanseAndCurateSuppliers** for **Name** and click **OK**.</span></span>

6.  <span data-ttu-id="b406f-111">**솔루션 탐색기** 창에서 **Package.dtsx** 를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-111">In **Solution Explorer** window, right-click **Package.dtsx** and select **Rename**.</span></span> <span data-ttu-id="b406f-112">**솔루션 탐색기** 창이 표시 되지 않으면 메뉴 모음에서 **보기** 를 클릭 하 고 **솔루션 탐색기**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-112">If you don't see **Solution Explorer** window, click **View** on the menu bar and click **Solution Explorer**.</span></span>

     <span data-ttu-id="b406f-113">![Package.dtsx - 이름 바꾸기 메뉴](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - 이름 바꾸기 메뉴")</span><span class="sxs-lookup"><span data-stu-id="b406f-113">![Package.dtsx - Rename Menu](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Rename Menu")</span></span>

7.  <span data-ttu-id="b406f-114">**CleanseAndCurate.dtsx** 를 입력하고 **Enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-114">Type **CleanseAndCurate.dtsx** and press **ENTER**.</span></span> <span data-ttu-id="b406f-115">**확장명** 이 **.dtsx**인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b406f-115">Make sure that the **extension** remains **.dtsx**.</span></span>

## <a name="next-step"></a><span data-ttu-id="b406f-116">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b406f-116">Next Step</span></span>
 [<span data-ttu-id="b406f-117">태스크 5: Data Flow Task 추가</span><span class="sxs-lookup"><span data-stu-id="b406f-117">Task 5: Adding Data Flow Task</span></span>](task-5-adding-data-flow-task.md)


