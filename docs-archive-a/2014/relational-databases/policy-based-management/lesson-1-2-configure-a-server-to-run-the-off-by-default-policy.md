---
title: Off By Default 정책을 실행하도록 서버 구성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0842a30b7d0bbcd1b01ee9e98ed1ed9a74f0f35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646964"
---
# <a name="configure-a-server-to-run-the-off-by-default-policy"></a><span data-ttu-id="4e523-102">Off By Default 정책을 실행하도록 서버 구성</span><span class="sxs-lookup"><span data-stu-id="4e523-102">Configure a Server to Run the Off By Default Policy</span></span>
  <span data-ttu-id="4e523-103">이제 Off By Default라는 정책이 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-103">Now you have a policy named Off By Default.</span></span> <span data-ttu-id="4e523-104">이 태스크에서는 서버가 이 정책의 요구 사항을 준수하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-104">In this task, you will check to see whether your server complies with the requirements of this policy.</span></span>  
  
### <a name="to-run-the-off-by-default-policy"></a><span data-ttu-id="4e523-105">Off By Default 정책을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="4e523-105">To run the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="4e523-106">개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 마우스 오른쪽 단추로 클릭하고 **정책**을 가리킨 다음 **평가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-106">In Object Explorer, right-click your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], point to **Policies**, and then click **Evaluate**.</span></span>  
  
2.  <span data-ttu-id="4e523-107">**정책 평가** 대화 상자에서는 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 또는 파일에서 정책을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-107">In the **Evaluate Policies** dialog box you can select policies from another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or from a file.</span></span> <span data-ttu-id="4e523-108">이 단계를 위해서 **원본** 을 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스로 설정해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-108">For this step, leave **Source** set to your instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
3.  <span data-ttu-id="4e523-109">**정책** 섹션에서 **Off By Default** 정책을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-109">In the **Policies** section, select the **Off By Default** policy.</span></span>  
  
4.  <span data-ttu-id="4e523-110">서버가 정책을 준수하는지 여부를 확인하려면 **평가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-110">To see whether the server is in compliance with the policy, click **Evaluate**.</span></span>  
  
5.  <span data-ttu-id="4e523-111">**이 정책을 준수하는 경우** 결과 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 영역에 확인 표시가 있는 녹색 원이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-111">In the **Results** area, you will see a green circle with a check mark if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] complies with the policy.</span></span> <span data-ttu-id="4e523-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 이 정책을 준수하지 않는 경우 X 표시가 있는 빨간색 원이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-112">You will see a red circle with an X if the [!INCLUDE[ssDE](../../includes/ssde-md.md)] does not comply with the policy.</span></span>  
  
6.  <span data-ttu-id="4e523-113">오류가 발생할 경우 **대상 정보** 영역의 **메시지** 열에서 추가 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-113">In the **Target Details** area, you will see additional information in the **Message** column if an error occurs.</span></span> <span data-ttu-id="4e523-114">**메시지** 열에서 **보기** 를 클릭하여 검사한 각 패싯 속성에 대한 검사 결과를 포함하는 보고서를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-114">In the **Message** column, click **View** to see a report that contains the results of the check for each facet property that was checked.</span></span>  
  
7.  <span data-ttu-id="4e523-115">정책 설명이 페이지 아래쪽에 표시되고 **추가 도움말** 섹션에서 정책에 대해 구성한 하이퍼링크를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-115">The policy description is displayed at the bottom of the page, and the **Additional help** section displays the hyperlink that you have configured for the policy.</span></span> <span data-ttu-id="4e523-116">메시지 하이퍼링크를 클릭하여 정책을 만들 때 지정한 웹 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-116">Click the message hyperlink to open the Web page that you specified when you created the policy.</span></span>  
  
8.  <span data-ttu-id="4e523-117">브라우저를 닫은 다음 **결과 자세히 보기** 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-117">Close the browser, and then close the **Results Detailed View** dialog box.</span></span>  
  
9. <span data-ttu-id="4e523-118">서버가 정책을 준수하지 않고, 데이터베이스 메일을 사용하지 않으려는 경우 **평가 결과** 페이지에서 **적용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-118">If the server is out of compliance and you want to disable Database Mail, click **Apply** in the **Evaluation Results** page.</span></span>  
  
10. <span data-ttu-id="4e523-119">**결과 자세히 보기** 대화 상자와 **정책 평가** 대화 상자를 모두 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4e523-119">Close both the **Results Detailed View** and the **Evaluate Policies** dialog boxes.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="4e523-120">다음 단원</span><span class="sxs-lookup"><span data-stu-id="4e523-120">Next Lesson</span></span>  
 [<span data-ttu-id="4e523-121">2단원: 명명 표준 정책 만들기 및 적용</span><span class="sxs-lookup"><span data-stu-id="4e523-121">Lesson 2: Create and Apply a Naming Standards Policy</span></span>](lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
