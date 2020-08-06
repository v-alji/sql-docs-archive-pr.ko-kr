---
title: 스키마 옵션 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735208"
---
# <a name="specify-schema-options"></a><span data-ttu-id="fe14b-102">스키마 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="fe14b-102">Specify Schema Options</span></span>
  <span data-ttu-id="fe14b-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 스키마 옵션을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-103">This topic describes how to specify schema options in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="fe14b-104">테이블 또는 뷰를 게시하는 경우 게시된 개체에 대해 복제되는 개체 작성 옵션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-104">When you are publishing a table or view, you can control the object creation options that are replicated for the published object.</span></span> <span data-ttu-id="fe14b-105">아티클을 만들 때 이 옵션을 설정할 수 있으며 나중에 이 옵션을 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-105">You can set these option when the article is created, and you can also change them at a later time.</span></span> <span data-ttu-id="fe14b-106">아티클에 대해 이 옵션을 명시적으로 지정하지 않으면 기본 옵션 집합이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-106">If you do not explicitly specify these options for an article, a default set of options will be defined.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe14b-107">복제 저장 프로시저를 사용할 때의 기본 스키마 옵션은 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 사용하여 아티클을 추가할 때의 기본 옵션과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-107">The default schema options when using replication stored procedures may differ from the default options when articles are added using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="fe14b-108">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="fe14b-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="fe14b-109">**시작하기 전 주의 사항:**</span><span class="sxs-lookup"><span data-stu-id="fe14b-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="fe14b-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fe14b-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="fe14b-111">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fe14b-111">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="fe14b-112">**스키마 옵션을 지정하려면:**</span><span class="sxs-lookup"><span data-stu-id="fe14b-112">**To specify schema options, using:**</span></span>  
  
     [<span data-ttu-id="fe14b-113">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="fe14b-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="fe14b-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="fe14b-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fe14b-115">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="fe14b-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="fe14b-116">제한 사항</span><span class="sxs-lookup"><span data-stu-id="fe14b-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="fe14b-117">게시가 만들어진 후 스키마 옵션을 변경하면 새 스냅샷을 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-117">If you change schema options after a publication is created, you must generate a new snapshot.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="fe14b-118">권장 사항</span><span class="sxs-lookup"><span data-stu-id="fe14b-118">Recommendations</span></span>  
  
-   <span data-ttu-id="fe14b-119">스키마 옵션의 전체 목록은 [transact-sql&#41;&#40;sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 의 \*\* \@ schema_option\*\* 매개 변수를 참조 하 고 sp_addmergearticle [&#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fe14b-119">For the complete list of schema options, see the **\@schema_option** parameter of [sp_addarticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="fe14b-120">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="fe14b-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="fe14b-121">제약 조건 및 트리거를 구독자에 복사할지 여부 등의 스키마 옵션을 **아티클 속성-\<Article>** 대화 상자의 **속성** 탭에 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-121">Specify schema options, such as whether to copy constraints and triggers to Subscribers, on the **Properties** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="fe14b-122">이 탭은 새 게시 마법사 및 **게시 속성 - \<Publication>** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-122">This tab is available in the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="fe14b-123">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](create-a-publication.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-123">For more information about using the wizard and accessing the dialog box, see [Create a Publication](create-a-publication.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-schema-options"></a><span data-ttu-id="fe14b-124">스키마 옵션을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="fe14b-124">To specify schema options</span></span>  
  
1.  <span data-ttu-id="fe14b-125">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 아티클을 선택하고 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-125">On the **Articles** Page of the New Publication Wizard or **Publication Properties - \<Publication>** dialog box, select an article, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="fe14b-126">스키마 옵션 변경 내용을 적용할 아티클을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-126">Select which articles schema option changes should apply to:</span></span>  
  
    -   <span data-ttu-id="fe14b-127">**선택한 \<ObjectType> 아티클 속성 설정**을 클릭하여 **아티클 속성 - \<ObjectName>** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 **아티클** 페이지의 개체 창에 강조 표시된 개체에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-127">Click **Set Properties of Highlighted \<ObjectType> Article** to launch the **Article Properties - \<ObjectName>** dialog box; property changes made in this dialog box are applied only to the object that is highlighted in the object pane on the **Articles** page.</span></span>  
  
    -   <span data-ttu-id="fe14b-128">**모든 \<ObjectType> 아티클 속성 설정**을 클릭하여 **모든 \<ObjectType> 아티클 속성** 대화 상자를 엽니다. 이 대화 상자에서 변경한 속성은 **아티클** 페이지의 개체 창에서 해당 형식을 갖는 모든 개체(아직 게시용으로 선택하지 않은 개체 포함)에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-128">Click **Set Properties of All \<ObjectType> Articles** to launch the **Properties for All \<ObjectType> Articles** dialog box; property changes made in this dialog box are applied to all objects of that type in the object pane on the **Articles** page, including ones not yet selected for publication.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fe14b-129">**모든 \<ObjectType> 아티클의 속성** 대화 상자에서 변경한 속성은 이전에 **아티클 속성 - \<ObjectName>** 대화 상자에서 지정한 내용을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-129">Property changes made in the **Properties for All \<ObjectType> Articles** dialog box override any made previously in the **Article Properties - \<ObjectName>** dialog box.</span></span> <span data-ttu-id="fe14b-130">예를 들어 특정 개체 유형의 모든 아티클에 대해 여러 기본값을 설정하고 개별 개체에 대해 일부 속성도 설정하려면 먼저 모든 아티클의 기본값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-130">If, for example, you want to set a number of defaults for all articles of an object type, but also want to set some properties for individual objects, set the defaults for all articles first.</span></span> <span data-ttu-id="fe14b-131">그런 다음 개별 개체에 대해 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-131">Then set the properties for the individual objects.</span></span>  
  
3.  <span data-ttu-id="fe14b-132">**아티클 속성 - \<Article>** 대화 상자의 **속성** 탭에 있는 **구독자에 개체 및 설정 복사** 및 **대상 개체** 섹션에서 옵션에 대한 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-132">In the **Copy Objects and Settings to Subscriber** and **Destination Object** sections of the **Properties** tab of the **Article Properties - \<Article>** dialog box, specify values for the options.</span></span>  
  
4.  <span data-ttu-id="fe14b-133">필요한 경우 속성을 수정한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-133">Modify any properties if necessary, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="fe14b-134">**게시 속성 - \<Publication>** 대화 상자에서 **확인**을 클릭하여 저장하고 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-134">If you are in the **Publication Properties - \<Publication>** dialog box, click **OK** to save and close the dialog box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="fe14b-135">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="fe14b-135">Using Transact-SQL</span></span>  
 <span data-ttu-id="fe14b-136">스키마 옵션은 하나 이상의 옵션에 대한 [|(비트 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 결과인 16진수 값으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-136">Schema options are specified as a hexadecimal value that is the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more options.</span></span> <span data-ttu-id="fe14b-137">자세한 내용은 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 및 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-137">For more information, see [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) and [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe14b-138">비트 연산을 수행하기 전에 스키마 옵션 값을 **binary** 에서 **int** 로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-138">You must convert schema option values from **binary** to **int** before performing a bitwise operation.</span></span> <span data-ttu-id="fe14b-139">자세한 내용은 [CAST 및 CONVERT&#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-139">For more information, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a><span data-ttu-id="fe14b-140">스냅샷 또는 트랜잭션 게시에 대한 아티클을 정의할 때 스키마 옵션을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="fe14b-140">To specify schema options when defining an article for a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="fe14b-141">게시 데이터베이스의 게시자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-141">At the Publisher on the publication database, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="fe14b-142">\*\* \@ 게시**에 대해 아티클이 속한 게시의 이름, \*\* \@ 아티클**용 아티클의 이름, \*\* \@ source_object**에 대해 게시 되는 데이터베이스 개체, \*\* \@ 형식**에 대 한 데이터베이스 개체의 유형 및 |를 지정 합니다. [ (비트 or)](/sql/t-sql/language-elements/bitwise-or-transact-sql) \*\* \@ schema_option\*\*에 대 한 하나 이상의 스키마 옵션의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-142">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, the type of database object for **\@type**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="fe14b-143">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-143">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a><span data-ttu-id="fe14b-144">병합 게시에 대한 아티클을 정의할 때 스키마 옵션을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="fe14b-144">To specify schema options when defining an article for a merge publication</span></span>  
  
1.  <span data-ttu-id="fe14b-145">게시 데이터베이스의 게시자에서 [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-145">At the Publisher on the publication database, execute [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).</span></span> <span data-ttu-id="fe14b-146">\*\* \@ 게시**에 대해 아티클이 속한 게시의 이름 \*\* \@ , 아티클의 아티클 이름,** \*\* \@ source_object**에 대해 게시 되는 데이터베이스 개체 및 [| (비트 or)](/sql/t-sql/language-elements/bitwise-or-transact-sql) \*\* \@ schema_option**에 대 한 하나 이상의 스키마 옵션의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-146">Specify the name of the publication to which the article belongs for **\@publication**, a name for the article for **\@article**, the database object being published for **\@source_object**, and the [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) result of one or more schema options for **\@schema_option**.</span></span> <span data-ttu-id="fe14b-147">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-147">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a><span data-ttu-id="fe14b-148">스냅샷 또는 트랜잭션 게시의 기존 아티클에 대한 스키마 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="fe14b-148">To change schema options for an existing article in a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="fe14b-149">게시 데이터베이스의 게시자에서 [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-149">At the Publisher on the publication database, execute [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql).</span></span> <span data-ttu-id="fe14b-150">\*\* \@ 게시\*\* 에 대해 아티클이 속한 게시의 이름과 \*\* \@ 아티클에\*\*대 한 아티클 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-150">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="fe14b-151">결과 집합에서 **schema_option** 열의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-151">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="fe14b-152">옵션이 설정되었는지 판단하기 위해 1단계의 값과 원하는 스키마 옵션 값을 사용하여 [&(비트 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 연산을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-152">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="fe14b-153">결과가 **0**이면 옵션이 설정되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-153">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="fe14b-154">결과가 옵션 값이면 옵션이 이미 설정된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-154">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="fe14b-155">옵션이 설정되지 않은 경우 1단계의 값과 원하는 스키마 옵션 값을 사용하여 [|(비트 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 연산을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-155">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="fe14b-156">게시 데이터베이스의 게시자에서 [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-156">At the Publisher on the publication database, execute [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql).</span></span> <span data-ttu-id="fe14b-157">\*\* \@ 게시**에 대해 아티클이 속한 게시의 이름, \*\* \@ 아티클의**아티클 이름, \*\* \@ 속성**에 **schema_option** 값, \*\* \@ 값**에 3 단계의 16 진수 결과를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-157">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="fe14b-158">스냅샷 에이전트를 실행하여 새 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-158">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="fe14b-159">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-159">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a><span data-ttu-id="fe14b-160">병합 게시의 기존 아티클에 대한 스키마 옵션을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="fe14b-160">To change schema options for an existing article in a merge publication</span></span>  
  
1.  <span data-ttu-id="fe14b-161">게시 데이터베이스의 게시자에서 [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-161">At the Publisher on the publication database, execute [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql).</span></span> <span data-ttu-id="fe14b-162">\*\* \@ 게시\*\* 에 대해 아티클이 속한 게시의 이름과 \*\* \@ 아티클에\*\*대 한 아티클 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-162">Specify the name of the publication to which the article belongs for **\@publication** and the name of the article for **\@article**.</span></span> <span data-ttu-id="fe14b-163">결과 집합에서 **schema_option** 열의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-163">Note the value of the **schema_option** column in the result set.</span></span>  
  
2.  <span data-ttu-id="fe14b-164">옵션이 설정되었는지 판단하기 위해 1단계의 값과 원하는 스키마 옵션 값을 사용하여 [&(비트 AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) 연산을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-164">Execute a [& (Bitwise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql) operation using the value from step 1 and the desired schema option value to determine if the option is set.</span></span>  
  
    -   <span data-ttu-id="fe14b-165">결과가 **0**이면 옵션이 설정되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-165">If the result is **0**, the option is not set.</span></span>  
  
    -   <span data-ttu-id="fe14b-166">결과가 옵션 값이면 옵션이 이미 설정된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-166">If the result is the option value, the option is already set.</span></span>  
  
3.  <span data-ttu-id="fe14b-167">옵션이 설정되지 않은 경우 1단계의 값과 원하는 스키마 옵션 값을 사용하여 [|(비트 OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) 연산을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-167">If the option is not set, execute a [| (Bitwise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) operation using the value from step 1 and the desired schema option value.</span></span>  
  
4.  <span data-ttu-id="fe14b-168">게시 데이터베이스의 게시자에서 [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-168">At the Publisher on the publication database, execute [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql).</span></span> <span data-ttu-id="fe14b-169">\*\* \@ 게시**에 대해 아티클이 속한 게시의 이름, \*\* \@ 아티클의**아티클 이름, \*\* \@ 속성**에 **schema_option** 값, \*\* \@ 값**에 3 단계의 16 진수 결과를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-169">Specify the name of the publication to which the article belongs for **\@publication**, the name of the article for **\@article**, a value of **schema_option** for **\@property**, and the hexadecimal result from step 3 for **\@value**.</span></span>  
  
5.  <span data-ttu-id="fe14b-170">스냅샷 에이전트를 실행하여 새 스냅샷을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="fe14b-170">Run the Snapshot Agent to generate a new snapshot.</span></span> <span data-ttu-id="fe14b-171">자세한 내용은 [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe14b-171">For more information, see [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe14b-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe14b-172">See Also</span></span>  
 <span data-ttu-id="fe14b-173">[데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="fe14b-173">[Publish Data and Database Objects](publish-data-and-database-objects.md) </span></span>  
 [<span data-ttu-id="fe14b-174">Article Options for Transactional Replication</span><span class="sxs-lookup"><span data-stu-id="fe14b-174">Article Options for Transactional Replication</span></span>](../transactional/article-options-for-transactional-replication.md)  
  
  
