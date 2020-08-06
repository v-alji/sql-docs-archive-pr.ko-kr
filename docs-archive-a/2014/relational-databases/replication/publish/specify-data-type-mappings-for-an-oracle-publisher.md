---
title: Oracle 게시자에 대한 데이터 형식 매핑 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], data type mapping
- data types [SQL Server replication], Oracle publishing
- mapping data types [SQL Server replication]
ms.assetid: f172d631-3b8c-4912-bd0f-568366cd9870
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 26331e3864940b9c7f2a2588e3d3cbfa9944c900
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736168"
---
# <a name="specify-data-type-mappings-for-an-oracle-publisher"></a><span data-ttu-id="e0d6a-102">Oracle 게시자에 대한 데이터 형식 매핑 지정</span><span class="sxs-lookup"><span data-stu-id="e0d6a-102">Specify Data Type Mappings for an Oracle Publisher</span></span>
  <span data-ttu-id="e0d6a-103">이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]의 Oracle 게시자에 대한 데이터 형식 매핑을 지정하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-103">This topic describes how to specify data type mappings for an Oracle Publisher in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="e0d6a-104">Oracle 게시자에 대해 기본 데이터 형식 매핑 집합이 제공되지만 특정 게시에 대해 다른 매핑을 지정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-104">Although a set of default data type mappings are provided for Oracle Publishers, it might be necessary to specify different mappings for a given publication.</span></span>  
  
 <span data-ttu-id="e0d6a-105">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="e0d6a-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="e0d6a-106">**다음을 사용하여 Oracle게시자에 대한 데이터 형식 매핑을 지정하려면**</span><span class="sxs-lookup"><span data-stu-id="e0d6a-106">**To specify data type mappings for an Oracle Publisher, using:**</span></span>  
  
     [<span data-ttu-id="e0d6a-107">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e0d6a-107">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e0d6a-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e0d6a-108">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e0d6a-109">SQL Server Management Studio 사용</span><span class="sxs-lookup"><span data-stu-id="e0d6a-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e0d6a-110">**아티클 속성 - \<Article>** 대화 상자의 **데이터 매핑** 탭에서 데이터 형식 매핑을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-110">Specify data type mappings on the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box.</span></span> <span data-ttu-id="e0d6a-111">이 옵션은 새 게시 마법사의 **아티클** 페이지 및 **게시 속성 - \<Publication>** 대화 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-111">This is available from the **Articles** page of the New Publication Wizard and the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="e0d6a-112">마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [Oracle 데이터베이스에서 게시 만들기](create-a-publication-from-an-oracle-database.md) 및 [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-112">For more information about using the wizard and accessing the dialog box, see [Create a Publication from an Oracle Database](create-a-publication-from-an-oracle-database.md) and [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-specify-a-data-type-mapping"></a><span data-ttu-id="e0d6a-113">데이터 형식 매핑을 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e0d6a-113">To specify a data type mapping</span></span>  
  
1.  <span data-ttu-id="e0d6a-114">새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<Publication>** 대화 상자에서 테이블을 선택한 다음 **아티클 속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-114">On the **Articles** page of the New Publication Wizard or the **Publication Properties - \<Publication>** dialog box, select a table, and then click **Article Properties**.</span></span>  
  
2.  <span data-ttu-id="e0d6a-115">**선택한 테이블 아티클 속성 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-115">Click **Set Properties of Highlighted Table Article**.</span></span>  
  
3.  <span data-ttu-id="e0d6a-116">**아티클 속성 - \<Article>** 대화 상자의 **데이터 매핑** 탭에서 **구독자 데이터 형식** 열의 매핑을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-116">On the **Data Mapping** tab of the **Article Properties - \<Article>** dialog box, select mappings from the **Subscriber Data Type** column:</span></span>  
  
    -   <span data-ttu-id="e0d6a-117">하나의 매핑만 사용할 수 있는 데이터 형식의 경우 속성 표의 열이 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-117">For some data types there is only one possible mapping, in which case the column in the property grid is read-only.</span></span>  
  
    -   <span data-ttu-id="e0d6a-118">일부 형식의 경우 두 개 이상의 매핑을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-118">For some types, there is more than one type that you can select.</span></span> [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="e0d6a-119">는 애플리케이션에 다른 매핑이 필요 하지 않는 한 기본 매핑을 사용할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-119">recommends that you use the default mapping unless your application requires a different mapping.</span></span> <span data-ttu-id="e0d6a-120">자세한 내용은 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-120">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e0d6a-121">Transact-SQL 사용</span><span class="sxs-lookup"><span data-stu-id="e0d6a-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="e0d6a-122">복제 저장 프로시저를 사용하여 사용자 지정 데이터 형식 매핑을 프로그래밍 방식으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-122">You can specify custom data type mappings programmatically using replication stored procedures.</span></span> <span data-ttu-id="e0d6a-123">또한 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 와 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] DBMS (데이터베이스 관리 시스템) 간에 데이터 형식을 매핑할 때 사용 되는 기본 매핑을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-123">You can also set the default mappings that are used when mapping data types between [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and a non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database management system (DBMS).</span></span> <span data-ttu-id="e0d6a-124">자세한 내용은 [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-124">For more information, see [Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md).</span></span>  
  
#### <a name="to-define-custom-data-type-mappings-when-creating-an-article-belonging-to-an-oracle-publication"></a><span data-ttu-id="e0d6a-125">Oracle 게시에 속한 아티클을 작성할 때 사용자 지정 데이터 형식 매핑을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e0d6a-125">To define custom data type mappings when creating an article belonging to an Oracle publication</span></span>  
  
1.  <span data-ttu-id="e0d6a-126">Oracle 게시가 아직 없는 경우 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-126">If one does not already exist, create an Oracle publication.</span></span>  
  
2.  <span data-ttu-id="e0d6a-127">배포자에서 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-127">At the Distributor, execute [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).</span></span> <span data-ttu-id="e0d6a-128">**\@use_default_datatypes**에 **0** 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-128">Specify a value of **0** for **\@use_default_datatypes**.</span></span> <span data-ttu-id="e0d6a-129">자세한 내용은 [아티클을 정의](define-an-article.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-129">For more information, see [Define an Article](define-an-article.md).</span></span>  
  
3.  <span data-ttu-id="e0d6a-130">배포자에서 [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) 를 실행하여 게시된 아티클의 열에 대한 기존 매핑을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-130">At the Distributor, execute [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) to view the existing mapping for a column in a published article.</span></span>  
  
4.  <span data-ttu-id="e0d6a-131">배포자에서 [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-131">At the Distributor, execute [sp_changearticlecolumndatatype](/sql/relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql).</span></span> <span data-ttu-id="e0d6a-132">**\@publisher**에 Oracle 게시자의 이름을 지정하고 **\@publication**, **\@article** 및 **\@column**을 지정하여 게시된 열을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-132">Specify the name of the Oracle Publisher for **\@publisher**, as well as **\@publication**, **\@article**, and **\@column** to define the published column.</span></span> <span data-ttu-id="e0d6a-133">**\@type**에 매핑할 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 형식의 이름을 지정하고 해당되는 경우 **\@length**, **\@precision** 및 **\@scale**을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-133">Specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type to map to for **\@type**, as well as **\@length**, **\@precision**, and **\@scale**, where applicable.</span></span>  
  
5.  <span data-ttu-id="e0d6a-134">배포자에서 [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-134">At the Distributor, execute [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql).</span></span> <span data-ttu-id="e0d6a-135">이렇게 하면 Oracle 게시에서 스냅샷을 생성하는 데 사용되는 뷰가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-135">This creates the view used to generate the snapshot from the Oracle publication.</span></span>  
  
#### <a name="to-specify-a-mapping-as-the-default-mapping-for-a-data-type"></a><span data-ttu-id="e0d6a-136">매핑을 데이터 형식에 대한 기본 매핑으로 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e0d6a-136">To specify a mapping as the default mapping for a data type</span></span>  
  
1.  <span data-ttu-id="e0d6a-137">(옵션) 데이터베이스의 배포자에서 [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-137">(Optional) At the Distributor on any database, execute [sp_getdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql).</span></span> <span data-ttu-id="e0d6a-138">**\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version**을 지정하고 원본 DBMS를 식별하는 데 필요한 기타 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-138">Specify **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_version**, and any other parameters needed to identify the source DBMS.</span></span> <span data-ttu-id="e0d6a-139">대상 DBMS의 현재 매핑된 데이터 형식에 대한 정보는 출력 매개 변수를 사용하여 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-139">Information on the currently mapped data type in the destination DBMS is returned using the output parameters.</span></span>  
  
2.  <span data-ttu-id="e0d6a-140">(옵션) 데이터베이스의 배포자에서 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-140">(Optional) At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="e0d6a-141">**\@source_dbms**를 지정하고 결과 집합을 필터링하는 데 필요한 기타 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-141">Specify **\@source_dbms** and any other parameters needed to filter the result set.</span></span> <span data-ttu-id="e0d6a-142">결과 집합에서 원하는 매핑에 대한 **mapping_id** 의 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-142">Note the value of **mapping_id** for the desired mapping in the result set.</span></span>  
  
3.  <span data-ttu-id="e0d6a-143">데이터베이스의 배포자에서 [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-143">At the Distributor on any database, execute [sp_setdefaultdatatypemapping](/sql/relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql).</span></span>  
  
    -   <span data-ttu-id="e0d6a-144">2단계에서 얻은 **mapping_id**의 원하는 값을 아는 경우 **\@mapping_id**에 이 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-144">If you know the desired value of **mapping_id** obtained in step 2, specify it for **\@mapping_id**.</span></span>  
  
    -   <span data-ttu-id="e0d6a-145">**mapping_id**를 모르는 경우 **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type** 매개 변수 및 기존 매핑을 식별하는 데 필요한 기타 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-145">If you do not know the **mapping_id**, specify the parameters **\@source_dbms**, **\@source_type**, **\@destination_dbms**, **\@destination_type**, and any other parameters required to identify an existing mapping.</span></span>  
  
#### <a name="to-find-valid-data-types-for-a-given-oracle-data-type"></a><span data-ttu-id="e0d6a-146">지정된 Oracle 데이터 형식에 대한 유효한 데이터 형식을 찾으려면</span><span class="sxs-lookup"><span data-stu-id="e0d6a-146">To find valid data types for a given Oracle data type</span></span>  
  
1.  <span data-ttu-id="e0d6a-147">데이터베이스의 배포자에서 [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql)을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-147">At the Distributor on any database, execute [sp_helpdatatypemap](/sql/relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql).</span></span> <span data-ttu-id="e0d6a-148">**\@source_dbms**의 값을 **ORACLE**로 지정하고 결과 집합을 필터링하는 데 필요한 기타 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-148">Specify a value of **ORACLE** for **\@source_dbms** and any other parameters needed to filter the result set.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="e0d6a-149">예(Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="e0d6a-149">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="e0d6a-150">다음 예에서는 열을 Oracle 데이터 형식 NUMBER로 변경하여 기본 `numeric` 데이터 형식 대신 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 숫자 데이터 형식 `float`(38,38)에 매핑되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-150">This example changes a column with an Oracle data type of NUMBER so it is mapped to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data type `numeric`(38,38), instead of the default data type `float`.</span></span>  
  
 [!code-sql[HowTo#sp_changecolumndatatype](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_changecolumndatatype)]  
  
 <span data-ttu-id="e0d6a-151">다음 쿼리 예에서는 Oracle 9 데이터 형식 `CHAR`에 대한 기본 및 대체 매핑을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-151">This example query returns the default and alternative mappings for the Oracle 9 data type `CHAR`.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_char](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_char)]  
  
 <span data-ttu-id="e0d6a-152">다음 쿼리 예에서는 소수 자릿수 또는 전체 자릿수 없이 지정된 경우 Oracle 9 데이터 형식 `NUMBER`에 대한 기본 매핑을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e0d6a-152">This example query returns the default mappings for the Oracle 9 data type `NUMBER` when it is specified without a scale or precision.</span></span>  
  
 [!code-sql[HowTo#sp_helpcolumndatatype_number](../../../snippets/tsql/SQL15/replication/howto/tsql/datatypemapping.sql#sp_helpcolumndatatype_number)]  
  
## <a name="see-also"></a><span data-ttu-id="e0d6a-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0d6a-153">See Also</span></span>  
 <span data-ttu-id="e0d6a-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="e0d6a-154">[Data Type Mapping for Oracle Publishers](../non-sql/data-type-mapping-for-oracle-publishers.md) </span></span>  
 <span data-ttu-id="e0d6a-155">[다른 유형의 데이터베이스 복제](../non-sql/heterogeneous-database-replication.md) </span><span class="sxs-lookup"><span data-stu-id="e0d6a-155">[Heterogeneous Database Replication](../non-sql/heterogeneous-database-replication.md) </span></span>  
 <span data-ttu-id="e0d6a-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="e0d6a-156">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="e0d6a-157">Oracle 게시자 구성</span><span class="sxs-lookup"><span data-stu-id="e0d6a-157">Configure an Oracle Publisher</span></span>](../non-sql/configure-an-oracle-publisher.md)  
  
  
