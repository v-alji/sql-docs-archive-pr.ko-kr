---
title: 도메인 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.kb.createdomain.f1
ms.assetid: 5c4828f5-bd51-4c29-b3de-87b7d2f2d3e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fad6abd795aa9412bb71d251623d92d3e13b889c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647265"
---
# <a name="create-a-domain"></a><span data-ttu-id="6bf9d-102">도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="6bf9d-102">Create a Domain</span></span>
  <span data-ttu-id="6bf9d-103">이 항목에서는 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )에서 도메인을 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-103">This topic describes how to create a domain in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).</span></span> <span data-ttu-id="6bf9d-104">도메인의 값은 필드의 데이터를 의미 체계에 따라 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-104">The values in the domain are a semantic representation of the data in a field.</span></span> <span data-ttu-id="6bf9d-105">도메인에 대한 자세한 내용은 [도메인 관리](../../2014/data-quality-services/managing-a-domain.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-105">For more information on domains, see [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md).</span></span>  
  
 <span data-ttu-id="6bf9d-106">새 도메인을 만드는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-106">There are two ways to create a new domain.</span></span> <span data-ttu-id="6bf9d-107">첫 번째는 새 기술 자료 또는 기존 기술 자료에 정보를 추가할 데이터 샘플을 분석하는 기술 자료 검색 작업의 매핑 단계에서 만드는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-107">The first is during the Map step of the knowledge discovery activity, when you are in the process of analyzing a data sample to add knowledge to a new or existing knowledge base.</span></span> <span data-ttu-id="6bf9d-108">두 번째는 도메인 관리 작업에서 기존 도메인을 변경하는 대신 새 도메인을 만드는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-108">The second is during the domain management activity, when instead of changing an existing domain, you create a new one.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6bf9d-109">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="6bf9d-109">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="6bf9d-110">필수 조건</span><span class="sxs-lookup"><span data-stu-id="6bf9d-110">Prerequisites</span></span>  
 <span data-ttu-id="6bf9d-111">도메인을 만들려면 기술 자료를 만들고 열어 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-111">To create a domain, you must have created and opened a knowledge base.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6bf9d-112">보안</span><span class="sxs-lookup"><span data-stu-id="6bf9d-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6bf9d-113">권한</span><span class="sxs-lookup"><span data-stu-id="6bf9d-113">Permissions</span></span>  
 <span data-ttu-id="6bf9d-114">도메인을 만들려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_administrator 역할이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-114">You must have the dqs_kb_editor role or the dqs_administrator on the DQS_MAIN database to create a domain.</span></span>  
  
##  <a name="create-a-domain-in-the-knowledge-discovery-activity"></a><a name="Discovery"></a> <span data-ttu-id="6bf9d-115">기술 자료 검색 작업에서 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="6bf9d-115">Create a Domain in the Knowledge Discovery Activity</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="6bf9d-116">[Data Quality Client 응용 프로그램을 실행](../../2014/data-quality-services/run-the-data-quality-client-application.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-116">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="6bf9d-117">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **기술 자료 열기** 를 클릭한 다음 기술 자료를 선택하거나 **새 기술 자료** 를 클릭하고 새 기술 자료의 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-117">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
3.  <span data-ttu-id="6bf9d-118">**기술 자료 검색** 을 작업으로 선택한 다음 **만들기** 를 클릭하여 새 기술 자료를 만들거나 **열기** 를 클릭하여 기존 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-118">Select **Knowledge Discovery** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
4.  <span data-ttu-id="6bf9d-119">**맵** 페이지에서 데이터 원본에 대한 연결을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-119">On the **Map** page, specify a connection to the data source.</span></span> <span data-ttu-id="6bf9d-120">자세한 내용은 [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-120">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md).</span></span>  
  
5.  <span data-ttu-id="6bf9d-121">**매핑** 테이블에서 빈 행의 **원본 열** 에 대한 드롭다운 목록에서 원본 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-121">In the **Mappings** table, select a source column from the drop-down list for the **Source Column** column of an empty row.</span></span> <span data-ttu-id="6bf9d-122">해당 도메인이 없으면 **도메인 만들기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-122">If no corresponding domain exists, click the **Create a Domain** icon.</span></span>  
  
##  <a name="create-a-domain-in-the-domain-management-activity"></a><a name="DomainManagement"></a><span data-ttu-id="6bf9d-123">도메인 관리 작업에서 도메인 만들기</span><span class="sxs-lookup"><span data-stu-id="6bf9d-123">Create a Domain in the Domain Management Activity</span></span>  
  
1.  <span data-ttu-id="6bf9d-124">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면에서 **기술 자료 열기** 를 클릭한 다음 기술 자료를 선택하거나 **새 기술 자료** 를 클릭하고 새 기술 자료의 속성을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-124">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Open knowledge base** and then select a knowledge base, or click **New knowledge base** and enter properties for the new knowledge base.</span></span>  
  
2.  <span data-ttu-id="6bf9d-125">**도메인 관리** 를 작업으로 선택한 다음 **만들기** 를 클릭하여 새 기술 자료를 만들거나 **열기** 를 클릭하여 기존 기술 자료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-125">Select **Domain Management** as the activity, and then click **Create** to create the new knowledge base or **Open** to open an existing knowledge base.</span></span>  
  
3.  <span data-ttu-id="6bf9d-126">**도메인 관리** 페이지에서 도메인 목록 위에 있는 **도메인 만들기** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-126">On the **Domain Management** page, click the **Create a Domain** icon above the Domain list.</span></span>  
  
##  <a name="set-domain-properties"></a><a name="Properties"></a><span data-ttu-id="6bf9d-127">도메인 속성 설정</span><span class="sxs-lookup"><span data-stu-id="6bf9d-127">Set Domain Properties</span></span>  
  
1.  <span data-ttu-id="6bf9d-128">**도메인 만들기** 대화 상자에서 기술 자료에 고유한 이름과 설명(최대 256자)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-128">In the **Create Domain** dialog box, enter a name that is unique to the knowledge base and a description up to 256 characters.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6bf9d-129"> 도메인 속성에 대한 자세한 내용은 [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-129">For more information about domain properties, see [Set Domain Properties](../../2014/data-quality-services/set-domain-properties.md).</span></span>  
  
2.  <span data-ttu-id="6bf9d-130">**데이터 형식** 목록에서 도메인 값의 데이터 형식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-130">From the **Data Type** list, select a data type for the values in the domain.</span></span> <span data-ttu-id="6bf9d-131">데이터 형식은 **문자열** (기본값), **날짜**, **정수**또는 **10진수**가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-131">The data type can be **String** (the default), **Date**, **Integer**, or **Decimal**.</span></span>  
  
3.  <span data-ttu-id="6bf9d-132">동의어 값 대신 동의어 그룹의 선행 값이 출력되도록 지정하려면 **선행 값 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-132">Select **Use Leading Values** to specify that the leading value in a group of synonyms will be output instead of a value that is a synonym to it.</span></span> <span data-ttu-id="6bf9d-133">각 동의어 값이 올바른 형식 또는 수정된 형식으로 출력되고 동의어 그룹의 선행 값으로 바뀌지 않도록 지정하려면 **선행 값 사용** 을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-133">Deselect **Use Leading Values** to specify that each synonym value is output in its correct or corrected form, and is not replaced by the leading value for its group.</span></span>  
  
4.  <span data-ttu-id="6bf9d-134">데이터 형식이 **문자열**인 경우 **문자열 정규화** 를 선택하여 도메인 값의 특수 문자를 제거하면 일치 확률을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-134">If the data type is **String**, select **Normalize String** to remove special characters in the domain values, which may improve the likelihood of matches.</span></span>  
  
5.  <span data-ttu-id="6bf9d-135">**출력 형식** 드롭다운 목록에서 도메인의 데이터 값이 출력될 때 적용할 서식을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-135">From the **Format Output to** drop-down list, select the formatting that will be applied when the data values in the domain are output.</span></span> <span data-ttu-id="6bf9d-136">서식은 다음 목록에 표시된 것처럼 2단계에서 선택한 데이터 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-136">The formatting is specific to the data type selected in step 2, as shown in the following list:</span></span>  
  
    -   <span data-ttu-id="6bf9d-137">문자열 값의 경우 문자열이 대문자, 소문자로 출력되거나 앞 글자만 대문자로 출력되도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-137">For a string value, you can specify that the string be output as upper case, lower case, or capitalized.</span></span>  
  
    -   <span data-ttu-id="6bf9d-138">날짜 값의 경우 년, 월, 일 형식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-138">For a date value, you can specify the format of the day, month, and year.</span></span>  
  
    -   <span data-ttu-id="6bf9d-139">정수 값의 경우 적용할 서식 마스크의 유형을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-139">For an integer value, you can specify the type of format mask to be applied.</span></span>  
  
    -   <span data-ttu-id="6bf9d-140">10진수 값의 경우 적용할 서식 마스크의 유형과 정확도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-140">For a decimal value, you can specify the accuracy and the type of format mask to be applied.</span></span>  
  
     <span data-ttu-id="6bf9d-141">**출력 형식** 드롭다운 목록에서 **없음** 을 선택하면 목록의 아무런 서식도 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-141">Selecting **None** in the **Format Output to** drop-down list means none of the formats in the list will be applied.</span></span>  
  
6.  <span data-ttu-id="6bf9d-142">데이터 형식이 **문자열**인 경우 **언어** 드롭다운 목록에서 맞춤법 검사기를 설정할 경우 적용할 맞춤법 검사기의 언어 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-142">If the data type is **String**, in the **Language** drop-down list, select which language version of the speller you want to apply if you enable the speller.</span></span>  
  
7.  <span data-ttu-id="6bf9d-143">데이터 형식이 **문자열**인 경우 도메인을 채울 때 모든 문자열 값에 대해 맞춤법 검사기를 실행하려면 **맞춤법 검사기 사용** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-143">If the data type is **String**, select **Enable Speller** to run the Speller on all string values when populating the domain.</span></span>  
  
8.  <span data-ttu-id="6bf9d-144">데이터 형식이 **문자열**인 경우 문자열 값의 구문 오류를 검사하지 않고 도메인을 채우려면 **구문 오류 알고리즘 사용 안 함** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-144">If the data type is **String**, select **Disable Syntax Error Algorithms** to populate the domain without checking string values for syntax errors.</span></span>  
  
9. <span data-ttu-id="6bf9d-145">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-145">Click **OK**.</span></span>  
  
10. <span data-ttu-id="6bf9d-146">**마침** 을 클릭하여 [도메인 관리 작업 종료](../../2014/data-quality-services/end-the-domain-management-activity.md)에 설명된 대로 도메인 관리 작업을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-146">Click **Finish** to complete the domain management activity, as described in [End the Domain Management Activity](../../2014/data-quality-services/end-the-domain-management-activity.md).</span></span>  
  
##  <a name="follow-up-after-creating-a-domain"></a><a name="FollowUp"></a> <span data-ttu-id="6bf9d-147">후속 작업: 도메인을 만든 후</span><span class="sxs-lookup"><span data-stu-id="6bf9d-147">Follow Up: After Creating a Domain</span></span>  
 <span data-ttu-id="6bf9d-148">도메인을 만든 후 도메인에 대해 다른 도메인 관리 태스크를 수행하거나, 기술 자료 검색을 수행하여 도메인에 정보를 추가하거나, 도메인에 일치 정책을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-148">After you create a domain, you can perform other domain management tasks on the domain, you can perform knowledge discovery to add knowledge to the domain, or you can add a matching policy to the domain.</span></span> <span data-ttu-id="6bf9d-149">자세한 내용은 [기술 자료 검색 수행](../../2014/data-quality-services/perform-knowledge-discovery.md), [도메인 관리](../../2014/data-quality-services/managing-a-domain.md) 또는 [일치 정책 만들기](../../2014/data-quality-services/create-a-matching-policy.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6bf9d-149">For more information, see [Perform Knowledge Discovery](../../2014/data-quality-services/perform-knowledge-discovery.md), [Managing a Domain](../../2014/data-quality-services/managing-a-domain.md), or [Create a Matching Policy](../../2014/data-quality-services/create-a-matching-policy.md).</span></span>  
  
  
