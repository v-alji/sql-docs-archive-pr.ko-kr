---
title: '작업 6: 동의어 설정 | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bde0c0ec7f230ba2325aa01328b191fd8fd67fa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639157"
---
# <a name="task-6-setting-synonyms"></a><span data-ttu-id="89e20-102">태스크 6: 동의어 설정</span><span class="sxs-lookup"><span data-stu-id="89e20-102">Task 6: Setting Synonyms</span></span>
  <span data-ttu-id="89e20-103">이 작업에서는 **Country** 도메인의 **USA**및 **United States** 두 도메인 값을 동의어로 설정하고 **United States** 를 선행 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-103">In this task, you set two domain values, **USA** and **United States**, of the **Country** domain as synonyms with **United States** as the leading value.</span></span> <span data-ttu-id="89e20-104">**Country** 도메인을 만들 때 **선행 값 사용** 옵션을 선택했기 때문에 **Country** 도메인의 모든 **USA** 값은 United States가 선행 값이므로 **United States** 로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-104">Since the **Use Leading Values** option was selected when creating the **Country** domain, any **USA** values for the **Country** domain will be output as **United States** (as United States is the leading value).</span></span> <span data-ttu-id="89e20-105">자세한 내용은 [도메인 값 변경](https://msdn.microsoft.com/library/hh510408.aspx) 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="89e20-105">See [Change Domain Values](https://msdn.microsoft.com/library/hh510408.aspx) for more details.</span></span>

1.  <span data-ttu-id="89e20-106">도메인 목록에서 **Country** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-106">Select **Country** from the list of domains.</span></span>

2.  <span data-ttu-id="89e20-107">**도메인 값** 탭으로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-107">Switch to the **Domain Values** tab.</span></span>

3.  <span data-ttu-id="89e20-108">도구 모음에서 **새 도메인 값 추가** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-108">Click **Add new domain value** button on the toolbar.</span></span>

4.  <span data-ttu-id="89e20-109">값에 **USA** 를 입력하고 **Enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-109">Type **USA** for the value and press **ENTER**.</span></span>

5.  <span data-ttu-id="89e20-110">Ctrl 또는 Shift 키를 사용해서 **United States** 및 **USA** 를 여러 개 선택하고, 선택한 항목을 마우스 오른쪽 단추로 클릭한 후 **동의어로 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-110">Multiselect **United States** and **USA** using CTRL or SHIFT keys, right-click the selected items, and then click **Set as Synonyms**.</span></span> <span data-ttu-id="89e20-111">DQS에서 이러한 값을 그룹화하고 값 중 하나를 나머지 값을 대체할 선행 값으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-111">DQS groups these values and designate one of the values as the leading value that the other values are replaced with.</span></span>

     <span data-ttu-id="89e20-112">![동의어로 설정 메뉴](../../2014/tutorials/media/et-settingsynonyms-01.jpg "동의어로 설정 메뉴")</span><span class="sxs-lookup"><span data-stu-id="89e20-112">![Set as Synonyms Menu](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Set as Synonyms Menu")</span></span>

6.  <span data-ttu-id="89e20-113">**United States** 가 선행 값으로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-113">Notice that **United States** is set as the leading value.</span></span> <span data-ttu-id="89e20-114">USA를 선행 값으로 지정하려면 USA를 마우스 오른쪽 단추로 클릭하고 **선행 값으로 설정** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-114">If you want USA to be the leading value, you can right-click on USA and select **Set as Leading** option.</span></span> <span data-ttu-id="89e20-115">이 자습서에서는 **United States** 를 선행 값으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="89e20-115">For this tutorial, we use **United States** as the leading value.</span></span>

     <span data-ttu-id="89e20-116">![미국과 USA를 동의어로 설정](../../2014/tutorials/media/et-settingsynonyms-02.jpg "미국과 USA를 동의어로 설정")</span><span class="sxs-lookup"><span data-stu-id="89e20-116">![United States and USA as Synonyms](../../2014/tutorials/media/et-settingsynonyms-02.jpg "United States and USA as Synonyms")</span></span>

## <a name="next-step"></a><span data-ttu-id="89e20-117">다음 단계</span><span class="sxs-lookup"><span data-stu-id="89e20-117">Next Step</span></span>
 [<span data-ttu-id="89e20-118">태스크 7: 복합 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="89e20-118">Task 7: Creating a Composite Domain</span></span>](../../2014/tutorials/task-7-creating-a-composite-domain.md)


