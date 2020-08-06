---
title: HOST_NAME 값 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67d01df05c8d56fd435eb0ee1b42ba2da6a312ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646881"
---
# <a name="host_name-values"></a><span data-ttu-id="a0129-102">HOST_NAME 값</span><span class="sxs-lookup"><span data-stu-id="a0129-102">HOST_NAME Values</span></span>
  <span data-ttu-id="a0129-103">매개 변수가 있는 필터가 포함된 병합 게시는 SUSER_SNAME() 함수 및/또는 HOST_NAME() 함수를 사용하여 데이터를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-103">Merge publications with parameterized filters use the SUSER_SNAME() function and/or the HOST_NAME() function to filter data.</span></span> <span data-ttu-id="a0129-104">함수는 새 게시 마법사 또는 **게시 속성** 대화 상자에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-104">The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="a0129-105">기본적으로 HOST_NAME() 함수는 게시자에 연결하는 컴퓨터 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-105">By default, the HOST_NAME() function returns the name of the computer connecting to the Publisher.</span></span> <span data-ttu-id="a0129-106">매개 변수가 있는 필터를 사용할 경우 이 마법사 페이지에서 값을 입력하여 이 값을 재정의하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-106">When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard.</span></span> <span data-ttu-id="a0129-107">그러면 HOST_NAME() 함수는 컴퓨터 이름 대신 사용자가 지정한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-107">The HOST_NAME() function then returns the value you specify rather than the name of the computer.</span></span> <span data-ttu-id="a0129-108">자세한 내용은 [매개 변수가 있는 행 필터](merge/parameterized-filters-parameterized-row-filters.md)의 “HOST_NAME() 값 재정의”를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a0129-108">For more information, see the "Overriding the HOST_NAME() Value" section of [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a0129-109">HOST_NAME()을 재정의할 경우 HOST_NAME() 함수에 대한 모든 호출은 사용자가 지정한 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-109">If you override HOST_NAME(), all calls to the HOST_NAME() function will return the value you specify.</span></span> <span data-ttu-id="a0129-110">다른 애플리케이션이 컴퓨터 이름을 반환하는 HOST_NAME()에 종속되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-110">Ensure that other applications are not depending on HOST_NAME() returning the computer name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="a0129-111">옵션</span><span class="sxs-lookup"><span data-stu-id="a0129-111">Options</span></span>  
 <span data-ttu-id="a0129-112">**구독 속성**</span><span class="sxs-lookup"><span data-stu-id="a0129-112">**Subscription properties**</span></span>  
 <span data-ttu-id="a0129-113">**HOST_NAME 값** 열에 각 구독자에 대한 값을 입력하거나 구독자 컴퓨터의 이름인 기본값을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a0129-113">Enter a value for each Subscriber in the **HOST_NAME Value** column or accept the default, which is the name of the Subscriber computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0129-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a0129-114">See Also</span></span>  
 <span data-ttu-id="a0129-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a0129-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="a0129-116">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="a0129-116">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="a0129-117">[끌어오기 구독 속성 보기 및 수정](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a0129-117">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="a0129-118">[밀어넣기 구독 속성 보기 및 수정](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a0129-118">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="a0129-119">[HOST_NAME&#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a0129-119">[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span></span>  
 [<span data-ttu-id="a0129-120">게시 구독</span><span class="sxs-lookup"><span data-stu-id="a0129-120">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
