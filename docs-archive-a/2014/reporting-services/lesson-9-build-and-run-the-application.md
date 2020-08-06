---
title: '9단원: 애플리케이션 빌드 및 실행 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 068deb075f0f60dde634ac29f6f8f934448dc6a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647502"
---
# <a name="lesson-9-build-and-run-the-application"></a><span data-ttu-id="91419-102">Lesson 9: Build and Run the Application</span><span class="sxs-lookup"><span data-stu-id="91419-102">Lesson 9: Build and Run the Application</span></span>
  <span data-ttu-id="91419-103">데이터 테이블에 대한 데이터 필터를 만든 후에는 웹 사이트 애플리케이션을 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="91419-103">After you create a data filter for the data table, your next step is to build and run the website application.</span></span>

### <a name="to-build-and-run-the-application"></a><span data-ttu-id="91419-104">애플리케이션을 빌드하고 실행하려면</span><span class="sxs-lookup"><span data-stu-id="91419-104">To build and run the application</span></span>

1.  <span data-ttu-id="91419-105">**Ctrl+F5** 를 눌러 Default.aspx 페이지를 디버그하지 않고 실행하거나 F5 키를 눌러 해당 페이지를 디버그하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="91419-105">Press **CTRL+F5** to run the Default.aspx page without debugging, or press F5 to run the page with debugging.</span></span>

     <span data-ttu-id="91419-106">빌드 프로세스의 일부로 보고서가 컴파일되고 보고서에 사용된 식의 구문 오류와 같은 발견된 오류가 모두 Visual Studio 창의 맨 아래에 있는 **태스크 목록** 에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="91419-106">As part of the build process, the report is compiled and any errors found (such as a syntax error in an expression used in the report) are added to the **Task List** that is located at the bottom of the Visual Studio window.</span></span>

     <span data-ttu-id="91419-107">브라우저에 웹 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91419-107">The webpage appears in the browser.</span></span> <span data-ttu-id="91419-108">ReportViewer 컨트롤에 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91419-108">The ReportViewer control displays the report.</span></span> <span data-ttu-id="91419-109">도구 모음을 사용하여 보고서를 검색하고 확대/축소하고 Excel로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91419-109">You can use the toolbar to browse through the report, zoom, and export the report to Excel.</span></span>

2.  <span data-ttu-id="91419-110">마우스를 **이름** 열 아래의 행 위로 가져갑니다.</span><span class="sxs-lookup"><span data-stu-id="91419-110">Hover the mouse over any of the rows under **Name** column.</span></span> <span data-ttu-id="91419-111">마우스 커서에 손 모양 기호가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91419-111">The mouse cursor will display a Hand symbol.</span></span>

3.  <span data-ttu-id="91419-112">**이름** 열에서 값을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="91419-112">Click a value in the **Name** column.</span></span> <span data-ttu-id="91419-113">자식 보고서가 필터링된 해당 데이터와 함께 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="91419-113">The child report is shown with the corresponding filtered data.</span></span>

4.  <span data-ttu-id="91419-114">**ReportViewer**도구 모음에서 **부모 보고서로 돌아가기** 아이콘을 클릭하여 다시 **부모** 보고서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="91419-114">Click the icon, **Go back to parent report**, in the **ReportViewer** tool bar to navigate back to the **Parent** report.</span></span>

     <span data-ttu-id="91419-115">![ReportViewer를 사용 하 여 ssrs 드릴스루](../../2014/tutorials/media/ssrs-drillthrough-report.png "ReportViewer를 사용 하 여 ssrs 드릴스루")</span><span class="sxs-lookup"><span data-stu-id="91419-115">![ssrs drill through using ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs drill through using ReportViewer")</span></span>

5.  <span data-ttu-id="91419-116">브라우저를 닫아 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="91419-116">Close the browser to exit.</span></span>


