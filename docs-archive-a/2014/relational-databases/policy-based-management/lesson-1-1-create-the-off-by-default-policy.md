---
title: Off By Default 정책 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 98fde3c5-297c-4d95-981e-95700bbf5ccd
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 16d0893c155627a41149263b5ce7b21a4a217b74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646965"
---
# <a name="create-the-off-by-default-policy"></a><span data-ttu-id="e6444-102">Off By Default 정책 만들기</span><span class="sxs-lookup"><span data-stu-id="e6444-102">Create the Off By Default Policy</span></span>
  <span data-ttu-id="e6444-103">이 태스크에서는 노출 영역 구성 패싯을 기반으로 하는 Mail Off라는 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-103">This task creates a condition named Mail Off that is based on the Surface Area Configuration facet.</span></span> <span data-ttu-id="e6444-104">그리고 나서 Off By Default라는 정책을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-104">Then, it creates a policy named Off By Default.</span></span>  
  
### <a name="to-create-the-mail-off-condition"></a><span data-ttu-id="e6444-105">Mail Off 조건을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6444-105">To create the Mail Off condition</span></span>  
  
1.  <span data-ttu-id="e6444-106">개체 탐색기에서 **관리**, **정책 관리**, **패싯**을 차례로 확장하고 **노출 영역 구성**을 마우스 오른쪽 단추로 클릭한 다음 **새 조건**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-106">In Object Explorer, expand **Management**, expand **Policy Management**, expand **Facets**, right-click **Surface Area Configuration**, and then click **New Condition**.</span></span>  
  
2.  <span data-ttu-id="e6444-107">**새 조건 만들기** 대화 상자의 **이름** 상자에 **Mail Off**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-107">In the **Create New Condition** dialog box, in the **Name** box, type **Mail Off**.</span></span>  
  
3.  <span data-ttu-id="e6444-108">**패싯** 상자에서 **노출 영역 구성** 패싯이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-108">In the **Facet** box, confirm that **Surface Area Configuration** facet is selected.</span></span>  
  
4.  <span data-ttu-id="e6444-109">**식** 영역의 **필드** 상자에서 \*\* \@ Databasemailenabled\*\*를 선택 하 고, **연산자** 상자에서 **=** 를 선택 하 고, **값** 에서 **False**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-109">In the **Expression** area, in the **Field** box, select **\@DatabaseMailEnabled**, in the **Operator** box select **=**, and in the **Value** select **False**.</span></span>  
  
5.  <span data-ttu-id="e6444-110">**설명** 페이지에서 조건에 대한 설명을 입력한 다음 **확인** 을 클릭하여 조건을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-110">On the **Description** page, type a description of the condition, and then click **OK** to create the condition.</span></span>  
  
### <a name="to-create-the-off-by-default-policy"></a><span data-ttu-id="e6444-111">Off By Default 정책을 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6444-111">To create the Off By Default policy</span></span>  
  
1.  <span data-ttu-id="e6444-112">개체 탐색기에서 **노출 영역 구성**을 마우스 오른쪽 단추로 클릭한 다음 **새 정책**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-112">In Object Explorer, right-click **Surface Area Configuration**, and then click **New Policy**.</span></span>  
  
2.  <span data-ttu-id="e6444-113">**새 정책 만들기** 대화 상자의 **이름** 상자에 **Off By Default**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-113">In the **Create New Policy** dialog box, in the **Name** box, type **Off By Default**.</span></span>  
  
3.  <span data-ttu-id="e6444-114">**사용** 확인란을 선택하지 않은 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-114">Leave the **Enabled** checkbox unchecked.</span></span> <span data-ttu-id="e6444-115">**사용** 확인란은 자동화된 정책에 적용되며 이 정책은 요청 시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-115">The **Enabled** checkbox applies to automated policies, and this policy will be executed on demand.</span></span>  
  
4.  <span data-ttu-id="e6444-116">**조건 확인** 확인란에서 **노출 영역 구성** 영역까지 아래로 스크롤한 다음 **Mail Off** 를 확인할 조건으로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-116">In the **Check condition** checkbox, scroll down to the **Surface Area Configuration** area, and then select **Mail Off** as the condition to check.</span></span>  
  
5.  <span data-ttu-id="e6444-117">이 정책은 서버 범위 정책이므로 **적용 대상** 상자는 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-117">The **Against targets** box will be blank because this is a server-scoped policy.</span></span>  
  
6.  <span data-ttu-id="e6444-118">**평가 모드** 확인란에서 **요청 시** 를 평가 모드로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-118">In the **Evaluation Mode** checkbox, select **On demand** as the evaluation mode.</span></span>  
  
7.  <span data-ttu-id="e6444-119">**서버 제한** 확인란에서 **없음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-119">In the **Server restriction** checkbox, select **None**.</span></span>  
  
8.  <span data-ttu-id="e6444-120">**설명** 페이지에서 정책에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-120">On the **Description** page, type a description of the policy.</span></span>  
  
9. <span data-ttu-id="e6444-121">**추가 도움말 하이퍼링크** 영역에 정책에 대한 웹 페이지의 하이퍼링크를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-121">You can provide a hyperlink to a Web page for your policies in the **Additional help hyperlink** area.</span></span> <span data-ttu-id="e6444-122">**표시할 텍스트** 상자에 하이퍼링크에 대해 표시할 텍스트를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-122">In the **Text to display** box, type the text that will appear for the hyperlink.</span></span>  
  
10. <span data-ttu-id="e6444-123">**주소** 상자에 회사의 IT 부서에 대한 홈페이지와 같이 도움말 페이지에 대한 하이퍼링크를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-123">In the **Address** box, type a hyperlink to a Help page, such as the home page for the IT department of your company.</span></span>  
  
11. <span data-ttu-id="e6444-124">웹 페이지를 열어 주소를 확인하려면 **링크 테스트**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e6444-124">To confirm the address by opening the Web page, click **Test Link**.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e6444-125">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="e6444-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e6444-126">Off By Default 정책을 실행하도록 서버 구성</span><span class="sxs-lookup"><span data-stu-id="e6444-126">Configure a Server to Run the Off By Default Policy</span></span>](lesson-1-2-configure-a-server-to-run-the-off-by-default-policy.md)  
  
  
