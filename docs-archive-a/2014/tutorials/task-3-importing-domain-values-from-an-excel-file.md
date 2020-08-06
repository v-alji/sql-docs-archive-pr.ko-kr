---
title: '태스크 3: Excel 파일에서 도메인 값 가져오기 | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 242e8309-1195-495b-9cd5-aa127748c185
ms.author: lle
author: lrtoyou1223
ms.openlocfilehash: 707a3925bb6d0014e2a1248f904123b076024e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647387"
---
# <a name="task-3-importing-domain-values-from-an-excel-file"></a><span data-ttu-id="f6b84-102">태스크 3: Excel 파일에서 도메인 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6b84-102">Task 3: Importing Domain Values from an Excel File</span></span>

  <span data-ttu-id="f6b84-103">이 작업에서는 Excel 파일의 워크시트에서 **State** 도메인에 대한 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-103">In this task, you import values for the **State** domain from a worksheet of an Excel file.</span></span>

1.  <span data-ttu-id="f6b84-104">**도메인 목록** 에서 **State**도메인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-104">Click **State** domain in the **Domain list**.</span></span>

2.  <span data-ttu-id="f6b84-105">**도메인 값** 탭이 오른쪽 창에 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-105">Ensure that the **Domain Values** tab is active in the right pane.</span></span>

3.  <span data-ttu-id="f6b84-106">오른쪽 창의 도구 모음에서 **값 가져오기** 단추 옆에 있는 **아래쪽 화살표** 를 클릭하고 **Excel에서 유효한 값 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-106">In the right pane, from the toolbar, click **down arrow** next to the **Import Values** button, and click **Import Valid Values from Excel**.</span></span>

     <span data-ttu-id="f6b84-107">![Excel에서 유효한 값 가져오기 메뉴](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Excel에서 유효한 값 가져오기 메뉴")</span><span class="sxs-lookup"><span data-stu-id="f6b84-107">![Import Valid Values from Excel Menu](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-01.jpg "Import Valid Values from Excel Menu")</span></span>

4.  <span data-ttu-id="f6b84-108">**찾아보기**를 클릭하고 **Suppliers.xls**를 선택한 후 **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-108">Click **Browse**, select **Suppliers.xls**, and click **Open**.</span></span>

5.  <span data-ttu-id="f6b84-109">**워크시트** 에 대해 **StatesToImport$** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-109">Select **StatesToImport$** for the **Worksheet**.</span></span>

     <span data-ttu-id="f6b84-110">![도메인 값 가져오기 대화 상자](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "도메인 값 가져오기 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="f6b84-110">![Import Domain Values Dialog Box](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-02.jpg "Import Domain Values Dialog Box")</span></span>

6.  <span data-ttu-id="f6b84-111">**확인** 을 클릭하여 **도메인 값 가져오기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-111">Click **OK** to close the **Import Domain Values** dialog box.</span></span> <span data-ttu-id="f6b84-112">가져온 모든 State 이름이 목록에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-112">You should see all the names of states you imported in the list.</span></span> <span data-ttu-id="f6b84-113">가져온 후에는 **새 항목만 표시** 옵션이 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-113">Notice that **Show Only New** option is automatically selected after importing.</span></span> <span data-ttu-id="f6b84-114">값을 가져올 때 목록에 이전 값이 표시 되지 않는 경우이 옵션은 가져온 후 자동으로 사용 하도록 설정 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-114">When you import values and you don't see the old values in the list, it is because this option is automatically enabled after importing.</span></span> <span data-ttu-id="f6b84-115">모든 값을 표시하려면 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-115">To see all the values, clear the check box.</span></span> <span data-ttu-id="f6b84-116">동일한 값 집합을 다시 가져올 경우, 도메인에 이미 있는 값은 가져오기가 다시 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6b84-116">If you import the same set of values again, none of the values are imported as they already exist in the domain.</span></span>

     <span data-ttu-id="f6b84-117">![도메인 값에 대한 새 확인란만 표시](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "도메인 값에 대한 새 확인란만 표시")</span><span class="sxs-lookup"><span data-stu-id="f6b84-117">![Show Only New Checkbox on Domain Values](../../2014/tutorials/media/et-importingdomainvaluesfromanexcelfile-03.jpg "Show Only New Checkbox on Domain Values")</span></span>

## <a name="next-step"></a><span data-ttu-id="f6b84-118">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f6b84-118">Next Step</span></span>
 [<span data-ttu-id="f6b84-119">태스크 4: 도메인 규칙 설정</span><span class="sxs-lookup"><span data-stu-id="f6b84-119">Task 4: Setting Domain Rules</span></span>](../../2014/tutorials/task-4-setting-domain-rules.md)


