---
title: 연결된 도메인 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.linkeddomain.f1
ms.assetid: fd99d422-c53d-4d7c-9cdd-303c703683b6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 17e91197ecb8cb6ad68769937a8d385d8c73a778
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649692"
---
# <a name="create-a-linked-domain"></a><span data-ttu-id="c7ec2-102">연결된 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="c7ec2-102">Create a Linked Domain</span></span>
  <span data-ttu-id="c7ec2-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )의 기술 자료에서 연결된 도메인을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-103">This topic describes how to create a linked domain in a knowledge base in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="c7ec2-104">이전의 다른 기존 도메인에서 연결된 도메인을 만들고 해당 도메인의 모든 값, 규칙 및 속성을 상속(이름 및 설명 제외)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-104">A linked domain is created from another, previously existing domain, and inherits all values, rules, and properties from the domain that it is linked to, with the exception of the name and the description.</span></span> <span data-ttu-id="c7ec2-105">연결된 도메인 집합을 하나로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-105">You can manage a set of linked domains as one.</span></span> <span data-ttu-id="c7ec2-106">하나의 도메인을 다른 도메인에 연결하여 다른 도메인의 콘텐츠를 상속하는 도메인을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-106">By linking one domain to the other, you create a domain that inherits its contents from another domain.</span></span>  
  
## <a name="scenarios"></a><span data-ttu-id="c7ec2-107">시나리오</span><span class="sxs-lookup"><span data-stu-id="c7ec2-107">Scenarios</span></span>  
 <span data-ttu-id="c7ec2-108">연결된 도메인은 다음 시나리오에서 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-108">Linked domains are particularly useful in the following scenarios.</span></span>  
  
### <a name="mapping-multiple-fields-to-domains-that-share-values-rules-and-properties"></a><span data-ttu-id="c7ec2-109">값, 규칙 및 속성을 공유하는 도메인에 여러 필드 매핑</span><span class="sxs-lookup"><span data-stu-id="c7ec2-109">Mapping multiple fields to domains that share values, rules, and properties</span></span>  
 <span data-ttu-id="c7ec2-110">두 필드를 같은 도메인에 매핑할 수 없지만 하나의 필드를 도메인에 매핑한 다음 두 번째 필드를 첫 번째 도메인과 연결된 도메인에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-110">You cannot map two fields to the same domain, but you could map one field to a domain and then map a second field to a domain linked to the first domain.</span></span> <span data-ttu-id="c7ec2-111">이러한 방식으로 이름 및 설명을 제외하고 콘텐츠 및 속성이 같은 두 개의 서로 다른 도메인에 필드를 매핑할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="c7ec2-111">Doing so maps the fields to two different domains that have the same contents and properties (except name and description).</span></span> <span data-ttu-id="c7ec2-112">자세한 내용은 [Map two fields to linked domains](#Map)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-112">For more information, see [Map two fields to linked domains](#Map).</span></span>  
  
### <a name="controlling-data-flow-to-composite-domains"></a><span data-ttu-id="c7ec2-113">복합 도메인에 대한 데이터 흐름 제어</span><span class="sxs-lookup"><span data-stu-id="c7ec2-113">Controlling data flow to composite domains</span></span>  
 <span data-ttu-id="c7ec2-114">연결된 도메인을 사용하여 필드와 복합 도메인 간의 데이터 흐름을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-114">Linked domains enable you to control the data flow between fields and composite domains.</span></span> <span data-ttu-id="c7ec2-115">한 필드의 데이터가 복합 도메인으로 이동하는 시점과 유사한 다른 필드의 데이터가 복합 도메인으로 이동하지 않는 시점을 차별화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-115">You can differentiate when data from one field flows into a composite domain, and when data from another, very similar field does not flow into the composite domain.</span></span> <span data-ttu-id="c7ec2-116">이 작업을 수행하려면 연결된 두 도메인 중 하나만 복합 도메인의 일부로 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-116">You do so by specifying that of two linked domains, one is part of a composite domain, and one is not.</span></span> <span data-ttu-id="c7ec2-117">도메인 뷰에서는 연결된 도메인이 서로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-117">From a domain perspective, linked domains are identical.</span></span> <span data-ttu-id="c7ec2-118">즉, 연결된 도메인에는 같은 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-118">They contain the same knowledge.</span></span> <span data-ttu-id="c7ec2-119">그러나 복합 도메인 뷰에서는 연결된 도메인이 서로 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-119">However, from a composite-domain perspective, linked domains are different.</span></span> <span data-ttu-id="c7ec2-120">한 도메인은 복합 도메인에 참여하지만 다른 도메인은 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-120">One participates in the composite domain; the other does not.</span></span>  
  
 <span data-ttu-id="c7ec2-121">예를 들어 고객 이름, 고객 성 및 아버지의 이름 필드가 포함된 레코드가 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-121">An example is a record that contains the following fields: Customer First Name, Customer Last Name, and Father's First Name.</span></span> <span data-ttu-id="c7ec2-122">고객 이름과 아버지의 이름을 둘 다 이름 도메인에 매핑하고 이름 도메인과 성 도메인을 전체 이름 복합 도메인의 일부로 지정한 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-122">Suppose you map both customer first name and father's first name to a First Name domain, and make the First Name domain and the Last Name domain a part of a Full Name composite domain.</span></span> <span data-ttu-id="c7ec2-123">이 경우의 문제는 아버지의 이름이 성 없이 복합 도메인에 추가된다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-123">The problem is that the father's first name will be added to the composite domain without a last name.</span></span> <span data-ttu-id="c7ec2-124">그러나 두 이름 필드를 각각 서로 다른 도메인에 연결하고 두 도메인을 연결한 경우 고객 이름 도메인은 전체 복합 도메인에 추가하고 아버지의 이름 필드는 복합 도메인에 추가하지 않을 수 있습니다. 이렇게 하면 아버지의 이름이 복합 도메인에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-124">If, however, you link each of the two first name fields to a domain, and link the two domains, then you can add the Customer First Name domain to the Full Name composite domain, and not add the Father's First Name field to the composite domain, thereby preventing the Father's First Name from being added to the composite domain.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c7ec2-125">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="c7ec2-125">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="c7ec2-126">필수 조건</span><span class="sxs-lookup"><span data-stu-id="c7ec2-126">Prerequisites</span></span>  
 <span data-ttu-id="c7ec2-127">연결된 도메인을 만들려면 연결할 기존 도메인과 기술 자료가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-127">To create a linked domain, you must have a knowledge base and an existing domain that you want to link to.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c7ec2-128">보안</span><span class="sxs-lookup"><span data-stu-id="c7ec2-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c7ec2-129">권한</span><span class="sxs-lookup"><span data-stu-id="c7ec2-129">Permissions</span></span>  
 <span data-ttu-id="c7ec2-130">연결된 도메인을 만들려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-130">You must have the dqs_kb_editor or the dqs_administrator role on the DQS_MAIN database to create a linked domain.</span></span>  
  
##  <a name="create-a-linked-domain"></a><a name="Create"></a><span data-ttu-id="c7ec2-131">연결 된 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="c7ec2-131">Create a Linked Domain</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="c7ec2-132">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-132">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="c7ec2-133">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 기술 자료를 열거나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-133">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, open or create a knowledge base.</span></span> <span data-ttu-id="c7ec2-134">**도메인 관리** 를 작업으로 선택한 다음 **열기** 또는 **만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-134">Select **Domain Management** as the activity, and then click **Open** or **Create**.</span></span> <span data-ttu-id="c7ec2-135">자세한 내용은 [기술 자료 만들기](../../2014/data-quality-services/create-a-knowledge-base.md) 또는 [기술 자료 열기](../../2014/data-quality-services/open-a-knowledge-base.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-135">For more information, see [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md) or [Open a Knowledge Base](../../2014/data-quality-services/open-a-knowledge-base.md).</span></span>  
  
3.  <span data-ttu-id="c7ec2-136">**도메인 관리** 페이지의 **도메인 목록** 에서 새 도메인을 연결할 도메인을 마우스 오른쪽 단추로 클릭한 다음 **연결된 도메인 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-136">From the **Domain list** on the **Domain Management** page, right-click the domain that you want to link a new domain to, and then click **Create Linked Domain**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c7ec2-137">연결된 도메인을 만드는 데에만 사용되는 아이콘은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-137">There is not an icon dedicated to creating a linked domain.</span></span> <span data-ttu-id="c7ec2-138">이 작업을 수행하려면 상황에 맞는 메뉴의 명령을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-138">You can only do so using the command in the context menu.</span></span>  
  
4.  <span data-ttu-id="c7ec2-139">**도메인 만들기** 대화 상자에서 기술 자료에 고유한 이름과 설명(최대 256자)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-139">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description of up to 256 characters.</span></span> <span data-ttu-id="c7ec2-140">연결된 도메인 이름이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-140">Verify that the name of the domain linked to is correct.</span></span>  
  
5.  <span data-ttu-id="c7ec2-141">**확인** 을 클릭하여 연결된 도메인 만들기를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-141">Click **OK** to complete creation of the linked domain.</span></span>  
  
6.  <span data-ttu-id="c7ec2-142">필요한 경우 도메인 속성 탭에서 연결된 도메인의 이름 또는 설명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-142">If necessary, you can change the name or description of the linked domain in the Domain Properties tab.</span></span>  
  
7.  <span data-ttu-id="c7ec2-143">**마침** 을 클릭하여 [도메인 관리 작업 종료](../../2014/data-quality-services/end-the-domain-management-activity.md)에 설명된 대로 도메인 관리 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-143">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="map-two-fields-to-linked-domains"></a><a name="Map"></a> <span data-ttu-id="c7ec2-144">Map two fields to linked domains</span><span class="sxs-lookup"><span data-stu-id="c7ec2-144">Map two fields to linked domains</span></span>  
  
1.  <span data-ttu-id="c7ec2-145">기술 자료 검색 작업에 대한 기술 자료를 열어 데이터베이스와 테이블 또는 뷰에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-145">Open a knowledge base to the knowledge discovery activity, and map the knowledge base to the database and table or view.</span></span>  
  
2.  <span data-ttu-id="c7ec2-146">필드 하나를 도메인에 매핑한 다음 두 번째 필드를 같은 도메인에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-146">Map one field to a domain, and then attempt to map a second field to the same domain.</span></span>  
  
3.  <span data-ttu-id="c7ec2-147">도메인이 이미 사용 중임을 나타내는 팝업이 표시되면 예를 클릭하여 연결된 도메인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-147">In the popup indicating that the domain is already in use, click Yes to create a linked domain.</span></span>  
  
4.  <span data-ttu-id="c7ec2-148">도메인 만들기 대화 상자에서 도메인 이름과 설명을 입력한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-148">In the Create Domain dialog box, enter a domain name and description, and then click OK.</span></span>  
  
##  <a name="follow-up-after-creating-a-linked-domain"></a><a name="FollowUp"></a> <span data-ttu-id="c7ec2-149">후속 작업: 연결된 도메인을 만든 후</span><span class="sxs-lookup"><span data-stu-id="c7ec2-149">Follow Up: After Creating a Linked Domain</span></span>  
 <span data-ttu-id="c7ec2-150">연결된 도메인을 만든 후 도메인에 대해 다른 도메인 관리 태스크를 수행하거나, 기술 자료 검색을 수행하여 도메인에 정보를 추가하거나, 도메인에 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-150">After you create a linked domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="c7ec2-151">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-151">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
##  <a name="behavior-of-a-linked-domain"></a><a name="Behavior"></a> <span data-ttu-id="c7ec2-152">연결된 도메인의 동작</span><span class="sxs-lookup"><span data-stu-id="c7ec2-152">Behavior of a Linked Domain</span></span>  
 <span data-ttu-id="c7ec2-153">연결된 도메인에 대한 설정을 다음과 같이 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-153">You can change the settings for a linked domain as follows:</span></span>  
  
-   <span data-ttu-id="c7ec2-154">연결된 도메인의 이름 및 설명을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-154">You can change the name and description of a linked domain.</span></span>  
  
-   <span data-ttu-id="c7ec2-155">**데이터 형식**, **선행 값 사용**또는 **출력 형식** 속성에 대한 도메인 속성을 변경하려면 연결한 도메인을 선택하고 해당 도메인에 대한 **도메인 속성** 탭에서 이러한 설정을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-155">To change the domain properties for the **Data Type**, **Use Leading Values**, or **Format Output To** properties, select the domain that you linked to, and change those settings in the **Domain Properties** tab for that domain.</span></span> <span data-ttu-id="c7ec2-156">연결된 도메인의 속성에서는 이러한 설정을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-156">You cannot change those settings in the properties of the linked domain.</span></span> <span data-ttu-id="c7ec2-157">자세한 내용은 [도메인 만들기](../../2014/data-quality-services/create-a-domain.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-157">For more information, see [Create a Domain](../../2014/data-quality-services/create-a-domain.md).</span></span>  
  
-   <span data-ttu-id="c7ec2-158">도메인 관리 페이지의 **참조 데이터**, **도메인 규칙**, **도메인 값**및 **용어 기반 관계** 탭에 있는 설정은 연결된 도메인 또는 연결된 대상 도메인에 대해 변경할 수 있으며 이러한 변경 내용은 다른 도메인에 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-158">Settings in the **Reference Data**, **Domain Rules**, **Domain Values**, and **Term-based Relations** tabs of the Domain Management page can be changed for either the linked domain or the domain that it was linked to, and the changes will be inherited by the other domain.</span></span>  
  
 <span data-ttu-id="c7ec2-159">연결된 도메인에는 다음과 같은 특성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-159">Linked domains have the following characteristics:</span></span>  
  
-   <span data-ttu-id="c7ec2-160">두 도메인의 연결을 해제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-160">You cannot unlink two domains.</span></span> <span data-ttu-id="c7ec2-161">연결을 제거하려면 연결된 도메인 중 하나를 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-161">To remove the link, delete one of the linked domains.</span></span>  
  
-   <span data-ttu-id="c7ec2-162">도메인 관리 페이지의 도메인 목록에서 연결된 도메인을 선택하면 **값** 테이블이 있는 창에서 연결된 도메인을 나타내는 문자열에 해당 도메인이 연결된 도메인임을 나타내는 표시가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-162">When you select a linked domain in the domain list of the Domain Management page, the string identifying the linked domain in the pane containing the **Value** table contains an indication that the domain is a linked domain.</span></span>  
  
-   <span data-ttu-id="c7ec2-163">다른 도메인이 연결되어 있는 도메인을 삭제하면 두 도메인이 모두 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-163">If you delete a domain that another domain is linked to, both domains will be deleted.</span></span> <span data-ttu-id="c7ec2-164">그러나 연결된 도메인을 삭제한 경우에는 연결된 대상 도메인은 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-164">You can, however, delete a linked domain, and the domain linked to will not be deleted.</span></span>  
  
-   <span data-ttu-id="c7ec2-165">연결된 도메인은 자체가 다른 도메인에 연결되어 있는 도메인에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-165">A linked domain cannot be linked to a domain that itself is linked to another domain.</span></span>  
  
-   <span data-ttu-id="c7ec2-166">복합 도메인에 대한 연결된 도메인 또는 연결된 복합 도메인을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-166">You cannot create a linked domain or a linked composite domain to a composite domain.</span></span>  
  
-   <span data-ttu-id="c7ec2-167">도메인 관리 탭 중 하나에서 연결된 도메인을 두 번 클릭하면 도메인이 편집할 수 있도록 열리고 이름 문자열에 해당 도메인이 연결된 도메인임을 알리는 표시가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c7ec2-167">When you double-click a linked domain in any of the Domain Management tabs, the domain will be opened to editing with an indication in the name string that it is a linked domain.</span></span>  
  
  
