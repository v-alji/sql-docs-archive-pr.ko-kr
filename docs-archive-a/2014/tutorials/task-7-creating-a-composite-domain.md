---
title: '태스크 7: 복합 도메인 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ae778647-1df0-4952-9a69-0ef6177eea9c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 42936d25e267bcad5ba8ae512750f9e12f041579
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639141"
---
# <a name="task-7-creating-a-composite-domain"></a><span data-ttu-id="b7c2d-102">태스크 7: 복합 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="b7c2d-102">Task 7: Creating a Composite Domain</span></span>
  <span data-ttu-id="b7c2d-103">이 작업에서는 **Address Line**, **City**, **State**및 **Zip** 도메인으로 구성 된 복합 도메인, **주소 유효성 검사**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-103">In this task, you create a composite domain, **Address Validation**, which comprises **Address Line**, **City**, **State**, and **Zip** domains.</span></span> <span data-ttu-id="b7c2d-104">복합 도메인을 사용하면 규칙에 여러 도메인이 포함되는 도메인 간 규칙을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-104">A composite domain lets you define a cross-domain rule that involves multiple domains in a rule.</span></span> <span data-ttu-id="b7c2d-105">복합 도메인에는 필드 값을 여러 도메인으로 구문 분석할 수 있는 등의 다른 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-105">There are other advantages to a composite domain such as being able to parse a field value into multiple domains.</span></span>  <span data-ttu-id="b7c2d-106">예를 들어 Full Name 필드에 대한 값을 각각 First Name, Middle Name 및 Last Name 도메인으로 구문 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-106">For example, a value for a Full Name field can be parsed into separate First Name, Middle Name, and Last Name domains.</span></span> <span data-ttu-id="b7c2d-107">이 자습서에서는 도메인 간 규칙만 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-107">In this tutorial, you only define a cross-domain rule.</span></span> <span data-ttu-id="b7c2d-108">자세한 내용은 [복합 도메인 관리](https://msdn.microsoft.com/library/hh510399.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-108">See [Managing a Composite Domain](https://msdn.microsoft.com/library/hh510399.aspx) for more details.</span></span>  
  
1.  <span data-ttu-id="b7c2d-109">왼쪽 창에서 도구 모음의 **복합 도메인 만들기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-109">In the left pane, click **Create a composite domain** button on the toolbar.</span></span>  
  
     <span data-ttu-id="b7c2d-110">![복합 도메인 만들기 도구 모음 단추](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "복합 도메인 만들기 도구 모음 단추")</span><span class="sxs-lookup"><span data-stu-id="b7c2d-110">![Create a Composite Domain Toolbar Button](../../2014/tutorials/media/et-creatingacompositedomain-01.jpg "Create a Composite Domain Toolbar Button")</span></span>  
  
2.  <span data-ttu-id="b7c2d-111">**복합 도메인 이름**에 대 한 **주소 유효성 검사** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-111">Enter **Address Validation** for the **Composite Domain Name**.</span></span>  
  
     <span data-ttu-id="b7c2d-112">![주소 유효성 검사 복합 도메인](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "주소 유효성 검사 복합 도메인")</span><span class="sxs-lookup"><span data-stu-id="b7c2d-112">![Address Validation Composite Domain](../../2014/tutorials/media/et-creatingacompositedomain-02.jpg "Address Validation Composite Domain")</span></span>  
  
3.  <span data-ttu-id="b7c2d-113">도메인 목록에서 **Address Line**, **City**, **State**및 **Zip** 을 선택 하 고 **오른쪽 화살표** 를 클릭 하 여 **복합 도메인 목록의 도메인** 에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-113">From the domain list select **Address Line**, **City**, **State**, and **Zip** and click **right arrow** to add them to the **Domains in Composite Domain** list.</span></span>  
  
4.  <span data-ttu-id="b7c2d-114">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b7c2d-114">Click **OK** to close the dialog box.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="b7c2d-115">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b7c2d-115">Next Step</span></span>  
 [<span data-ttu-id="b7c2d-116">태스크 8: 복합 도메인 규칙 만들기</span><span class="sxs-lookup"><span data-stu-id="b7c2d-116">Task 8: Creating a Composite Domain Rule</span></span>](../../2014/tutorials/task-8-creating-a-composite-domain-rule.md)  
  
  
