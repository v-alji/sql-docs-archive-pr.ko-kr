---
title: 전체 텍스트 검색에 사용할 동의어 사전 파일 구성 및 관리 | Microsoft 문서
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], configuring
- thesaurus [full-text search]
ms.assetid: 3ef96a63-8a52-45be-9a1f-265bff400e54
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 67f0a5af7be4f41ce33692e5f28ad5adf676980c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743183"
---
# <a name="configure-and-manage-thesaurus-files-for-full-text-search"></a><span data-ttu-id="c9f79-102">전체 텍스트 검색에 사용할 동의어 사전 파일 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="c9f79-102">Configure and Manage Thesaurus Files for Full-Text Search</span></span>
  <span data-ttu-id="c9f79-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 전체 텍스트 쿼리는 동의어 사전을 사용하여 사용자 지정 용어의 동의어를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], full-text queries can search for synonyms of user-specified terms through the use of a thesaurus.</span></span> <span data-ttu-id="c9f79-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *동의어 사전* 은 특정 언어에 대한 동의어 집합을 정의하는데,</span><span class="sxs-lookup"><span data-stu-id="c9f79-104">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *thesaurus* defines a set of synonyms for a specific language.</span></span> <span data-ttu-id="c9f79-105">시스템 관리자는 확장 집합과 교체 집합의 두 형식으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-105">System administrators can define two forms of synonyms: expansion sets and replacement sets.</span></span> <span data-ttu-id="c9f79-106">전체 텍스트 데이터에 맞게 동의어 사전을 개발하면 해당 데이터에 대한 전체 텍스트 쿼리의 범위를 효과적으로 넓힐 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-106">By developing a thesaurus tailored to your full-text data, you can effectively broaden the scope of full-text queries on that data.</span></span> <span data-ttu-id="c9f79-107">동의어 사전 검색은 모든 [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 쿼리와 FORMSOF THESAURUS 절을 지정하는 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 쿼리에 대해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-107">Thesaurus matching occurs for all [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) and [FREETEXTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) queries and for any [CONTAINS](/sql/t-sql/queries/contains-transact-sql) and [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) queries that specify the FORMSOF THESAURUS clause.</span></span>  
  
##  <a name="basic-tasks-for-setting-up-a-thesaurus-file"></a><a name="tasks"></a><span data-ttu-id="c9f79-108">동의어 사전 파일을 설정 하기 위한 기본 작업</span><span class="sxs-lookup"><span data-stu-id="c9f79-108">Basic Tasks for Setting Up a Thesaurus File</span></span>  
 <span data-ttu-id="c9f79-109">서버 인스턴스의 전체 텍스트 검색 쿼리가 지정된 언어에서 동의어를 찾도록 하려면 해당 언어에 대한 동의어 사전 매핑(동의어)을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-109">Before full-text search queries on your server instance can look for synonyms in a given language, you must define thesaurus mappings (synonyms) for that language.</span></span> <span data-ttu-id="c9f79-110">각 동의어 사전은 다음을 정의하도록 수동으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-110">Each thesaurus must be manually configured to define the following:</span></span>  
  
-   <span data-ttu-id="c9f79-111">분음 부호 설정</span><span class="sxs-lookup"><span data-stu-id="c9f79-111">Diacritics setting</span></span>  
  
     <span data-ttu-id="c9f79-112">지정 된 동의어 사전에 대 한 모든 검색 패턴은 물결표 ( **~** ), 악센트 표시 (**??**) 또는 움라우트 (**??**)와 같은 분음 부호를 구분 하거나 구분 하지 않습니다. 즉, 악센트를 *구분* 하거나 *악센트를 구분*하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-112">For a given thesaurus, all search patterns are either sensitive or insensitive to diacritical marks such as a tilde (**~**), acute accent mark (**??**), or umlaut (**??**) (that is, *accent sensitive* or *accent insensitive*).</span></span> <span data-ttu-id="c9f79-113">예를 들어 "caf???" 패턴을 지정 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-113">For example, suppose you specify the pattern "caf??"</span></span> <span data-ttu-id="c9f79-114">전체 텍스트 쿼리에서 다른 패턴으로 바꾸도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-114">to be replaced by other patterns in a full-text query.</span></span> <span data-ttu-id="c9f79-115">동의어 사전이 악센트를 구분 하지 않는 경우 전체 텍스트 검색은 "caf???" 패턴을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-115">If the thesaurus is accent-insensitive, full-text search replaces the patterns "caf??"</span></span> <span data-ttu-id="c9f79-116">및 "cafe" 패턴이 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-116">and "cafe".</span></span> <span data-ttu-id="c9f79-117">동의어 사전이 악센트를 구분 하는 경우 전체 텍스트 검색은 "caf???" 패턴만 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-117">If the thesaurus is accent-sensitive, full-text search replaces only the pattern "caf??".</span></span> <span data-ttu-id="c9f79-118">기본적으로 동의어 사전은 악센트를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-118">By default, a thesaurus is accent-insensitive.</span></span>  
  
-   <span data-ttu-id="c9f79-119">확장 집합</span><span class="sxs-lookup"><span data-stu-id="c9f79-119">Expansion set</span></span>  
  
     <span data-ttu-id="c9f79-120">확장 집합은 전체 텍스트 쿼리에 의해 서로 대체되는 "writer", "author" 및 "journalist"와 같은 동의어 그룹을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-120">An expansion set contains a group of synonyms such as "writer", "author", and "journalist" that are substituted for one another by a full-text query.</span></span> <span data-ttu-id="c9f79-121">확장 집합에 동의어에 대한 일치 항목이 있는 쿼리는 확장 집합의 다른 모든 동의어를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-121">Queries that contain a match for any synonym in an expansion set are expanded to include every other synonym in the expansion set.</span></span>  
  
     <span data-ttu-id="c9f79-122">자세한 내용은 이 항목의 뒷부분에 나오는 "확장 집합의 XML 구조"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9f79-122">For more information, see "XML Structure of an Expansion Set," later in this topic.</span></span>  
  
-   <span data-ttu-id="c9f79-123">교체 집합</span><span class="sxs-lookup"><span data-stu-id="c9f79-123">Replacement set</span></span>  
  
     <span data-ttu-id="c9f79-124">교체 집합에는 대체 집합으로 바꿀 텍스트 패턴이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-124">A replacement set contains a text pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="c9f79-125">예를 보려면 이 항목의 뒷부분에 나오는 "교체 집합의 XML 구조" 섹션을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c9f79-125">For an example, see the section "XML Structure of a Replacement Set" later in this topic.</span></span>  
  
  
##  <a name="initial-content-of-the-thesaurus-files"></a><a name="initial_thesaurus_files"></a><span data-ttu-id="c9f79-126">동의어 사전 파일의 초기 내용</span><span class="sxs-lookup"><span data-stu-id="c9f79-126">Initial Content of the Thesaurus Files</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c9f79-127">는 지원되는 각 언어당 하나의 XML 동의어 사전 파일을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-127">provides a set of XML thesaurus files, one for each supported language.</span></span> <span data-ttu-id="c9f79-128">이러한 파일은 기본적으로 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-128">These files are essentially empty.</span></span> <span data-ttu-id="c9f79-129">파일에는 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 동의어 사전에 공통적인 최상위 XML 구조와 주석 처리된 예제 동의어 사전만 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-129">They contain only the top-level XML structure that is common to all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] thesauruses and a commented-out sample thesaurus.</span></span>  
  
 <span data-ttu-id="c9f79-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 함께 출시되는 동의어 사전 파일에는 모두 다음 XML 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-130">The thesaurus files that are released with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all contain the following XML code:</span></span>  
  
```  
<XML ID="Microsoft Search Thesaurus">  
  
<!--  Commented out  
  
    <thesaurus xmlns="x-schema:tsSchema.xml">  
<diacritics_sensitive>0</diacritics_sensitive>  
        <expansion>  
            <sub>Internet Explorer</sub>  
            <sub>IE</sub>  
            <sub>IE5</sub>  
        </expansion>  
        <replacement>  
            <pat>NT5</pat>  
            <pat>W2K</pat>  
            <sub>Windows 2012</sub>  
        </replacement>  
        <expansion>  
            <sub>run</sub>  
            <sub>jog</sub>  
        </expansion>  
    </thesaurus>  
-->  
</XML>  
```  
  
  
##  <a name="location-of-the-thesaurus-files"></a><a name="location"></a><span data-ttu-id="c9f79-131">동의어 사전 파일의 위치</span><span class="sxs-lookup"><span data-stu-id="c9f79-131">Location of the Thesaurus Files</span></span>  
 <span data-ttu-id="c9f79-132">동의어 사전 파일의 기본 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-132">The default location of the thesaurus files is:</span></span>  
  
 <span data-ttu-id="c9f79-133">*<SQL_Server_data_files_path>* \MSSQL12. MSSQLSERVER\MSSQL\FTDATA</span><span class="sxs-lookup"><span data-stu-id="c9f79-133">*<SQL_Server_data_files_path>* \MSSQL12.MSSQLSERVER\MSSQL\FTDATA</span></span>\  
  
 <span data-ttu-id="c9f79-134">이 기본 위치에는 다음 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-134">This default location contains the following files:</span></span>  
  
-   <span data-ttu-id="c9f79-135">언어별 동의어 사전 파일</span><span class="sxs-lookup"><span data-stu-id="c9f79-135">Language-specific thesaurus files</span></span>  
  
     <span data-ttu-id="c9f79-136">설치 중에 빈 동의어 사전 파일이 앞서 언급된 위치에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-136">During setup, empty thesaurus files are installed in the above location.</span></span> <span data-ttu-id="c9f79-137">지원되는 각 언어에 대해 별도의 파일이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-137">A separate file is provided for each supported language.</span></span> <span data-ttu-id="c9f79-138">시스템 관리자는 이러한 파일을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-138">A system administrator can customize these files.</span></span>  
  
     <span data-ttu-id="c9f79-139">동의어 사전 파일의 기본 파일 이름은 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-139">The default file names of the thesaurus files use following format:</span></span>  
  
     <span data-ttu-id="c9f79-140">' ts ' + \<three-letter language-abbreviation> + ' .xml '</span><span class="sxs-lookup"><span data-stu-id="c9f79-140">'ts' + \<three-letter language-abbreviation> + '.xml'</span></span>  
  
     <span data-ttu-id="c9f79-141">지정된 언어에 대한 동의어 사전 파일의 이름은 레지스트리의 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev> 값에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-141">The name of the thesaurus file for a given language is specified in the registry in the following value HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<instance-name>\MSSearch\\<language-abbrev>.</span></span>  
  
-   <span data-ttu-id="c9f79-142">전역 동의어 사전 파일</span><span class="sxs-lookup"><span data-stu-id="c9f79-142">The global thesaurus file</span></span>  
  
     <span data-ttu-id="c9f79-143">빈 전역 동의어 사전 파일인 tsGlobal.xml</span><span class="sxs-lookup"><span data-stu-id="c9f79-143">An empty global thesaurus file, tsGlobal.xml.</span></span>  
  
 <span data-ttu-id="c9f79-144">레지스트리 키를 변경하여 동의어 사전 파일의 위치와 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-144">You can change the location and names of a thesaurus file by changing its registry key.</span></span> <span data-ttu-id="c9f79-145">각 언어에 대해 동의어 사전 파일의 위치는 레지스트리의 다음 값에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-145">For each language, the location of the thesaurus file is specified in the following value in the registry:</span></span>  
  
 <span data-ttu-id="c9f79-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/ \<instance name> /MSSearch/Language/ \<language-abbreviation> /TsaurusFile</span><span class="sxs-lookup"><span data-stu-id="c9f79-146">HKLM/SOFTWARE/Microsoft/Microsoft SQL Server/\<instance name>/MSSearch/Language/\<language-abbreviation>/TsaurusFile</span></span>  
  
 <span data-ttu-id="c9f79-147">전역 동의어 사전 파일은 LCID 0의 중립 언어에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-147">The global thesaurus file corresponds to the Neutral language with LCID 0.</span></span> <span data-ttu-id="c9f79-148">이 값은 관리자만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-148">This value can be changed by administrators only.</span></span>  
  
  
##  <a name="how-queries-use-thesaurus-files"></a><a name="how_queries_use_tf"></a><span data-ttu-id="c9f79-149">쿼리가 동의어 사전 파일을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="c9f79-149">How Queries Use Thesaurus Files</span></span>  
 <span data-ttu-id="c9f79-150">동의어 사전 쿼리는 언어별 동의어 사전과 전역 동의어 사전을 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-150">A thesaurus query uses both a language-specific thesaurus and the global thesaurus.</span></span> <span data-ttu-id="c9f79-151">이 쿼리는 먼저 언어별 파일을 조회한 다음 이미 로드되지 않은 경우 처리를 위해 해당 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-151">First, the query looks up the language-specific file and loads it for processing (unless it is already loaded).</span></span> <span data-ttu-id="c9f79-152">이 쿼리는 동의어 사전 파일의 확장 집합 규칙과 교체 집합 규칙으로 지정된 언어별 동의어를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-152">The query is expanded to include the language-specific synonyms specified by the expansion set and replacement set rules in the thesaurus file.</span></span> <span data-ttu-id="c9f79-153">그런 다음 전역 동의어 사전에 대해 이러한 단계가 반복됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-153">These steps are then repeated for the global thesaurus.</span></span> <span data-ttu-id="c9f79-154">그러나 용어가 이미 언어별 동의어 사전 파일에서 일치 항목의 일부인 경우 해당 용어는 전역 동의어 사전에서 일치 항목으로 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-154">However, if a term is already part of a match in the language specific thesaurus file, the term is ineligible for matching in the global thesaurus.</span></span>  
  
  
##  <a name="understanding-the-structure-of-a-thesaurus-file"></a><a name="structure"></a><span data-ttu-id="c9f79-155">동의어 사전 파일의 구조 이해</span><span class="sxs-lookup"><span data-stu-id="c9f79-155">Understanding the Structure of a Thesaurus File</span></span>  
 <span data-ttu-id="c9f79-156">각 동의어 사전 파일은 ID가 `Microsoft Search Thesaurus`인 XML 컨테이너와, 예제 동의어 사전을 포함하는 주석(`<!--` ... `-->`)을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-156">Each thesaurus file defines an XML container whose ID is `Microsoft Search Thesaurus`, and a comment, `<!--` ... `-->`, that contains a sample thesaurus.</span></span> <span data-ttu-id="c9f79-157">동의어 사전은 다음과 \<thesaurus> 같이 분음 부호 설정, 확장 집합, 교체 집합을 정의 하는 자식 요소의 샘플이 포함 된 요소에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-157">The thesaurus is defined in a \<thesaurus> element that contains samples of the child elements that define the diacritics setting, expansion sets, and replacement sets, as follows:</span></span>  
  
-   <span data-ttu-id="c9f79-158">분음 부호 설정의 XML 구조</span><span class="sxs-lookup"><span data-stu-id="c9f79-158">XML Structure of the Diacritical Setting</span></span>  
  
     <span data-ttu-id="c9f79-159">동의어 사전의 분음 부호 설정은 단일 <diacritics_sensitive> 요소에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-159">The diacritics setting of a thesaurus is specified in a single <diacritics_sensitive> element.</span></span> <span data-ttu-id="c9f79-160">이 요소는 다음과 같이 악센트 구분 여부를 제어하는 정수 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-160">This element contains an integer value that controls accent sensitivity, as follows:</span></span>  
  
    |<span data-ttu-id="c9f79-161">분음 부호 설정</span><span class="sxs-lookup"><span data-stu-id="c9f79-161">Diacritics Setting</span></span>|<span data-ttu-id="c9f79-162">값</span><span class="sxs-lookup"><span data-stu-id="c9f79-162">Value</span></span>|<span data-ttu-id="c9f79-163">XML</span><span class="sxs-lookup"><span data-stu-id="c9f79-163">XML</span></span>|  
    |------------------------|-----------|---------|  
    |<span data-ttu-id="c9f79-164">악센트 구분 안 함</span><span class="sxs-lookup"><span data-stu-id="c9f79-164">Accent insensitive</span></span>|<span data-ttu-id="c9f79-165">0</span><span class="sxs-lookup"><span data-stu-id="c9f79-165">0</span></span>|`<diacritics_sensitive>0</diacritics_sensitive>`|  
    |<span data-ttu-id="c9f79-166">악센트 구분</span><span class="sxs-lookup"><span data-stu-id="c9f79-166">Accent sensitive</span></span>|<span data-ttu-id="c9f79-167">1</span><span class="sxs-lookup"><span data-stu-id="c9f79-167">1</span></span>|`<diacritics_sensitive>1</diacritics_sensitive>`|  
  
    > [!NOTE]  
    >  <span data-ttu-id="c9f79-168">이 설정은 파일에서 한 번만 적용될 수 있으며 해당 파일의 모든 검색 패턴에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-168">This setting can only be applied one time in the file, and it applies to all search patterns in the file.</span></span> <span data-ttu-id="c9f79-169">개별 패턴에 대해서는 이 설정을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-169">This setting cannot be specified for individual patterns.</span></span>  
  
-   <span data-ttu-id="c9f79-170">확장 집합의 XML 구조</span><span class="sxs-lookup"><span data-stu-id="c9f79-170">XML Structure of an Expansion Set</span></span>  
  
     <span data-ttu-id="c9f79-171">각 확장 집합은 \<expansion> 요소로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-171">Each expansion set is enclosed within an \<expansion> element.</span></span> <span data-ttu-id="c9f79-172">이 요소 내에서 \<sub> 요소에 하나 이상의 대체 단어를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-172">Within this element, you specify one or more substitutions in a \<sub> element.</span></span> <span data-ttu-id="c9f79-173">확장 집합에 서로의 동의어인 대체 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-173">In the expansion set, you can specify a group of substitutions that are synonyms of each other.</span></span>  
  
     <span data-ttu-id="c9f79-174">예를 들어 "writer", "author" 및 "journalist" 대체 단어를 동의어로 처리하도록 확장 섹션을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-174">For example, you can edit the expansion section to treat the substitutions "writer", "author", and "journalist" as synonyms.</span></span> <span data-ttu-id="c9f79-175">하나의 대체 집합에 일치하는 항목이 있는 전체 텍스트 검색 쿼리는 확장 집합에 지정된 다른 모든 대체 단어를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-175">full-text search queries that contain matches in one substitution are expanded to include all other substitutions specified in the expansion set.</span></span> <span data-ttu-id="c9f79-176">따라서 위 예에서 "author"라는 단어에 대해 FORMS OF THESAURUS 또는 FREETEXT 쿼리를 실행하면 전체 텍스트 검색에 "writer" 및 "journalist"라는 단어를 포함하는 검색 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-176">Therefore, in the preceding example, when you issue a FORMS OF THESAURUS or a FREETEXT query for the word "author", full-text search also returns search results containing the words "writer" and "journalist".</span></span>  
  
     <span data-ttu-id="c9f79-177">다음은 위 예에 대한 확장 집합 섹션을 나타낸 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-177">This is what the expansion set section would look like for the above example:</span></span>  
  
    ```  
    <expansion>  
            <sub>writer</sub>  
            <sub>author</sub>  
            <sub>journalist</sub>  
    </expansion>  
    ```  
  
-   <span data-ttu-id="c9f79-178">교체 집합의 XML 구조</span><span class="sxs-lookup"><span data-stu-id="c9f79-178">XML Structure of a Replacement Set</span></span>  
  
     <span data-ttu-id="c9f79-179">각 교체 집합은 \<replacement> 요소로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-179">Each replacement set is enclosed within a \<replacement> element.</span></span> <span data-ttu-id="c9f79-180">이 요소 내에서 동의어당 하나씩 1개 이상의 패턴을 \<pat> 요소에 지정하고, 0개 이상의 대체 단어를 \<sub> 요소에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-180">Within this element you can specify one or more patterns in a \<pat> element and zero or more substitutions in \<sub> elements, one per synonym.</span></span> <span data-ttu-id="c9f79-181">대체 집합으로 바꿀 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-181">You can specify a pattern to be replaced by a substitution set.</span></span> <span data-ttu-id="c9f79-182">패턴 및 대체 집합에는 단어 또는 일련의 단어를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-182">Patterns and substitutions can contain a word, or a sequence of words.</span></span> <span data-ttu-id="c9f79-183">패턴에 지정된 대체 단어가 없는 경우 사용자 쿼리에서 해당 패턴이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-183">If there is no substitution specified for a pattern, it has the effect of removing the pattern from the user query.</span></span>  
  
     <span data-ttu-id="c9f79-184">예를 들어 'Win8' 패턴을 'Windows Server 2012' 또는 'Windows 8.0' 대체 단어로 바꾸는 쿼리를 원하는 경우</span><span class="sxs-lookup"><span data-stu-id="c9f79-184">For example, suppose you want queries for "Win8", the pattern, to be replaced by "Windows Server 2012" or "Windows 8.0", the substitutions.</span></span> <span data-ttu-id="c9f79-185">'Win8'에 대해 전체 텍스트 쿼리를 실행하면 전체 텍스트 검색에 'Server 2012' 또는 'Windows 8.0'd\을 포함하는 검색 결과만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-185">If you run a full-text query for "Win8", full-text search only returns search results containing "Windows Server 2012" or "Windows 8.0".</span></span> <span data-ttu-id="c9f79-186">'Win8'을 포함하는 결과는 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-186">It does not return results containing "Win8".</span></span> <span data-ttu-id="c9f79-187">이는 'Win8' 패턴이 'Windows Server 2012' 및 'Windows 8.0' 패턴으로 '바뀌었기' 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-187">This is because the pattern "Win8" has been "replaced" by the patterns "Windows Server 2012" and "Windows 8.0".</span></span>  
  
     <span data-ttu-id="c9f79-188">다음은 위 예에 대한 교체 집합 섹션을 나타낸 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-188">This is what the replacement set section would look like for the above example:</span></span>  
  
    ```  
    <replacement>  
            <pat>Win8</pat>  
            <sub>Windows Server 2012</sub>  
            <sub>Windows 8.0</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="c9f79-189">패턴이 유사하게 일치하는 두 개의 교체 집합이 있는 경우 두 개 중 더 긴 것이 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-189">If you have two replacement sets with similar patterns being matched, the longer of the two takes precedence.</span></span> <span data-ttu-id="c9f79-190">예를 들어 "Internet Explorer online community"에 대해 FORMS OF THESAURUS 쿼리를 실행하고 다음과 같은 교체 집합이 있는 경우 "Internet Explorer" 교체 집합이 "Internet" 교체 집합보다 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-190">For example, if you run a FORMS OF THESAURUS query for "Internet Explorer online community" and you have the following replacement sets, the "Internet Explorer" replacement set takes precedence over the "Internet" replacement set.</span></span> <span data-ttu-id="c9f79-191">따라서 쿼리가 "IE online community" 또는 "IE 9 online community"로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-191">The query will therefore be processed as "IE online community" or "IE 9 online community".</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet</pat>  
             <sub>intranet</sub>  
    </replacement>  
    ```  
  
     <span data-ttu-id="c9f79-192">and</span><span class="sxs-lookup"><span data-stu-id="c9f79-192">and</span></span>  
  
    ```  
    <replacement>  
             <pat>Internet Explorer</pat>  
             <sub>IE</sub>  
             <sub>IE 9</sub>  
    </replacement>  
    ```  
  
  
##  <a name="working-with-thesaurus-files"></a><a name="working_with_thesaurus_files"></a><span data-ttu-id="c9f79-193">동의어 사전 파일 작업</span><span class="sxs-lookup"><span data-stu-id="c9f79-193">Working with Thesaurus Files</span></span>  
 <span data-ttu-id="c9f79-194">**동의어 사전 파일을 편집하려면**</span><span class="sxs-lookup"><span data-stu-id="c9f79-194">**To edit a thesaurus file**</span></span>  
  
-   [<span data-ttu-id="c9f79-195">동의어 사전 파일 편집</span><span class="sxs-lookup"><span data-stu-id="c9f79-195">Editing a Thesaurus File</span></span>](#editing)  
  
 <span data-ttu-id="c9f79-196">**업데이트된 동의어 사전 파일을 로드하려면**</span><span class="sxs-lookup"><span data-stu-id="c9f79-196">**To load an updated thesaurus file**</span></span>  
  
-   [<span data-ttu-id="c9f79-197">sp_fulltext_load_thesaurus_file&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9f79-197">sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql)  
  
 <span data-ttu-id="c9f79-198">**단어 분리기, 동의어 사전 및 중지 목록 조합의 토큰화 결과를 보려면**</span><span class="sxs-lookup"><span data-stu-id="c9f79-198">**To view the tokenization result of a word breaker, thesaurus, and stoplist combination**</span></span>  
  
-   [<span data-ttu-id="c9f79-199">dm_fts_parser &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="c9f79-199">sys.dm_fts_parser &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="editing-a-thesaurus-file"></a><a name="editing"></a><span data-ttu-id="c9f79-200">동의어 사전 파일 편집</span><span class="sxs-lookup"><span data-stu-id="c9f79-200">Editing a Thesaurus File</span></span>  
 <span data-ttu-id="c9f79-201">지정된 언어에 대한 동의어 사전은 해당 동의어 사전 파일(XML 파일)을 편집하여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-201">The thesaurus for a given language can be configured by editing its thesaurus file (an XML file).</span></span> <span data-ttu-id="c9f79-202">설치 하는 동안에는 컨테이너와 주석 처리 된 sample 요소만 포함 된 빈 동의어 사전 파일이 \<xml> \<thesaurus> 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-202">During setup, empty thesaurus files that contain only the \<xml> container and a commented-out sample \<thesaurus> element are installed.</span></span> <span data-ttu-id="c9f79-203">동의어를 검색 하는 전체 텍스트 검색 쿼리가 제대로 작동 하려면 \<thesaurus> 동의어 집합을 정의 하는 실제 요소를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-203">In order for full-text search queries that look for synonyms to work properly, you must create an actual \<thesaurus> element that defines a set of synonyms.</span></span> <span data-ttu-id="c9f79-204">확장 집합과 교체 집합의 두 형식으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-204">You can define two forms of synonyms, expansion sets and replacement sets.</span></span>  
  
 <span data-ttu-id="c9f79-205">**동의어 사전 파일에 대한 제한 사항**</span><span class="sxs-lookup"><span data-stu-id="c9f79-205">**Restrictions for thesaurus files**</span></span>  
  
 <span data-ttu-id="c9f79-206">동의어 사전 파일 편집에는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-206">The following restrictions apply to editing a thesaurus file:</span></span>  
  
-   <span data-ttu-id="c9f79-207">동의어 사전 파일은 시스템 관리자만 업데이트, 수정 또는 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-207">Only system administrators can update, modify, or delete thesaurus files.</span></span>  
  
-   <span data-ttu-id="c9f79-208">텍스트 편집기 도구를 사용하여 동의어 사전 파일을 편집하는 경우 파일을 유니코드 형식으로 저장하고 바이트 순서 표시를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-208">When editing thesaurus files using text editor tools, the files must be saved in Unicode format, and Byte Order Marks must be specified.</span></span>  
  
-   <span data-ttu-id="c9f79-209">동의어 사전 항목은 비어 있거나 빈 문자열로 단어 분리될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-209">Thesaurus entries cannot be empty or word break to an empty string.</span></span>  
  
-   <span data-ttu-id="c9f79-210">문자 수가 512개보다 많은 구는 동의어 사전 파일에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-210">Phrases in the thesaurus file must be no longer than 512 characters.</span></span>  
  
-   <span data-ttu-id="c9f79-211">동의어 사전에는 확장 집합의 \<sub> 항목과 교체 집합의 \<pat> 요소 사이에 중복된 항목이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-211">A thesaurus must not contain any duplicate entries among the \<sub> entries of expansion sets and the \<pat> elements of replacement sets.</span></span>  
  
 <span data-ttu-id="c9f79-212">**동의어 사전 파일에 대한 권장 사항**</span><span class="sxs-lookup"><span data-stu-id="c9f79-212">**Recommendations for thesaurus files**</span></span>  
  
 <span data-ttu-id="c9f79-213">동의어 사전 파일의 항목에는 특수 문자를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-213">We recommend that entries in the thesaurus file contain no special characters.</span></span> <span data-ttu-id="c9f79-214">특수 문자와 관련하여 단어 분리기의 동작에 미묘한 부분이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-214">This is because word breakers have subtle behaviors with respect to special characters.</span></span> <span data-ttu-id="c9f79-215">동의어 사전 항목에 특수 문자가 포함된 경우 해당 항목과 함께 사용된 단어 분리기는 전체 텍스트 쿼리의 동작에 미묘한 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-215">If a thesaurus entry contains any special characters, word breakers used in combination with that entry can have subtle behavioral implications for a full-text query.</span></span>  
  
 <span data-ttu-id="c9f79-216">중지 단어는 전체 텍스트 인덱스에서 생략되므로 \<sub> 항목에는 중지 단어를 포함하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-216">We recommend that \<sub> entries contain no stopwords since stopwords are omitted from the full-text index.</span></span> <span data-ttu-id="c9f79-217">쿼리는 동의어 사전 파일의 \<sub> 항목을 포함하도록 확장되므로 \<sub> 항목에 중지 단어가 포함되어 있으면 쿼리 크기가 불필요하게 커지게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-217">Queries are expanded to include the \<sub> entries from a thesaurus file, and if a \<sub> entry contains stopwords, query size increases unnecessarily.</span></span>  
  
#### <a name="to-edit-a-thesaurus-file"></a><span data-ttu-id="c9f79-218">동의어 사전 파일을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="c9f79-218">To edit a thesaurus file</span></span>  
  
1.  <span data-ttu-id="c9f79-219">메모장에서 동의어 사전 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-219">Open the thesaurus file in Notepad.</span></span>  
  
2.  <span data-ttu-id="c9f79-220">동의어 사전 파일을 처음 편집하는 경우 파일의 시작 및 끝 부분에서 각각 다음 주석 줄을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-220">If you are editing the thesaurus file for the first time, remove the following comment lines at the beginning and end of the file, respectively:</span></span>  
  
    ```  
    <!--Commented out  
    -->  
    ```  
  
3.  <span data-ttu-id="c9f79-221">교체 집합이나 확장 집합을 추가, 수정 또는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-221">Add, modify, or delete a replacement set, or expansion set.</span></span>  
  
4.  <span data-ttu-id="c9f79-222">파일을 저장하고 메모장을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-222">Save the file and close Notepad.</span></span>  
  
5.  <span data-ttu-id="c9f79-223">동의어 사전 파일의 언어에 해당하는 LCID(로컬 식별자)를 지정하고 [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) 을 사용하여 동의어 사전 파일의 내용을 tempdb에 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-223">Use [sp_fulltext_load_thesaurus_file](/sql/relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql) to load the content of the thesaurus file into tempdb, specifying the local identifier (LCID) that corresponds to the language of the thesaurus file.</span></span> <span data-ttu-id="c9f79-224">예를 들어 영어 동의어 사전 파일 tsenu.xml의 경우 해당하는 LCID는 1033입니다.</span><span class="sxs-lookup"><span data-stu-id="c9f79-224">For example, for the English thesaurus file, tsenu.xml, the corresponding LCID is 1033.</span></span>  
  
    ```  
    USE AdventureWorks2012 ;  
    EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
    GO  
    ```  
  
  
## <a name="see-also"></a><span data-ttu-id="c9f79-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9f79-225">See Also</span></span>  
 <span data-ttu-id="c9f79-226">[CONTAINS&#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f79-226">[CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql) </span></span>  
 <span data-ttu-id="c9f79-227">[CONTAINSTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f79-227">[CONTAINSTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql) </span></span>  
 <span data-ttu-id="c9f79-228">[FREETEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f79-228">[FREETEXT &#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql) </span></span>  
 <span data-ttu-id="c9f79-229">[FREETEXTTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9f79-229">[FREETEXTTABLE &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql) </span></span>  
 [<span data-ttu-id="c9f79-230">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="c9f79-230">Full-Text Search</span></span>](full-text-search.md)  
  
  
