---
title: 검색 필터 구성 및 관리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653787"
---
# <a name="configure-and-manage-filters-for-search"></a><span data-ttu-id="660d6-102">검색 필터 구성 및 관리</span><span class="sxs-lookup"><span data-stu-id="660d6-102">Configure and Manage Filters for Search</span></span>
  <span data-ttu-id="660d6-103">`varbinary`, `varbinary(max)`, `image` 또는 `xml` 데이터 형식의 문서를 인덱싱하려면 추가 처리가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-103">Indexing documents in an `varbinary`, `varbinary(max)`, `image`, or `xml` data type column requires extra processing.</span></span> <span data-ttu-id="660d6-104">이러한 처리를 수행하려면 필터를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-104">This processing must be performed by a filter.</span></span> <span data-ttu-id="660d6-105">필터는 문서에서 서식이 제거된 텍스트 정보를 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-105">The filter extracts the textual information from the document (removing the formatting).</span></span> <span data-ttu-id="660d6-106">그런 다음 필터는 테이블 열과 연결된 언어의 단어 분리기 구성 요소에 텍스트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-106">The filter then sends the text to the word-breaker component for the language associated with the table column.</span></span>  
  
 <span data-ttu-id="660d6-107">지정된 필터는 지정된 문서 유형(.doc, .pdf, .xls, .xml 등)에만 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-107">A given filter is specific to a given document type (.doc, .pdf, .xls, .xml, and so forth).</span></span> <span data-ttu-id="660d6-108">이러한 필터는 IFilter 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-108">These filters implement the IFilter interface.</span></span> <span data-ttu-id="660d6-109">이러한 문서 유형에 대한 자세한 내용을 보려면 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 카탈로그 뷰를 쿼리하세요.</span><span class="sxs-lookup"><span data-stu-id="660d6-109">For more information about these document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="660d6-110">이진 문서는 단일 `varbinary(max)` 또는 `image` 열에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-110">Binary documents can be stored in a single `varbinary(max)` or `image` column.</span></span> <span data-ttu-id="660d6-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 각 문서에 대해 파일 확장명을 기준으로 사용할 필터를 정확히 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-111">For each document, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chooses the correct filter based on the file extension.</span></span> <span data-ttu-id="660d6-112">파일이 또는 열에 저장 된 경우 파일 확장명이 표시 되지 않으므로 `varbinary(max)` `image` 파일 확장명 (.doc, .xls, .pdf 등)을 테이블의 별도 열 (형식 열 이라고 함)에 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-112">Because the file extension is not visible when the file is stored in a `varbinary(max)` or `image` column, the file extension (.doc, .xls,  .pdf, and so forth) must be stored in a separate column in the table, called a type column.</span></span> <span data-ttu-id="660d6-113">이 형식 열은 모든 문자 기반 데이터 형식이 될 수 있고 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word 문서를 나타내는 .doc와 같은 문서 파일 확장명을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-113">This type column can be of any character-based data type and contains the document file extension, such as .doc for a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word document.</span></span> <span data-ttu-id="660d6-114">의 **document** 테이블에서 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] **document** 열은 형식이 `varbinary(max)` 고 **fileextension**유형 열은 형식입니다 `nvarchar(8)` .</span><span class="sxs-lookup"><span data-stu-id="660d6-114">In the **Document** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], the **Document** column is of type `varbinary(max)`, and the type column, **FileExtension**, is of type `nvarchar(8)`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="660d6-115">필터 구현에 따라 필터에서 부모 개체에 포함된 개체를 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-115">A filter might be able to handle objects embedded in the parent object, depending on its implementation.</span></span> <span data-ttu-id="660d6-116">그러나 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 다른 개체에 대한 링크를 따라가도록 필터를 구성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-116">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not configure filters to follow links to other objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="660d6-117">에서는 고유한 XML 및 HTML 필터를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-117">installs its own XML and HTML filters.</span></span> <span data-ttu-id="660d6-118">또한 운영 체제에 설치되어 있는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 소유 형식(.doc, .xdoc, .ppt 등)용 필터도  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-118">In addition, any filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] proprietary formats (.doc, .xdoc, .ppt and so on) that are already installed on the operating system are also loaded by  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="660d6-119">현재 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에 로드되어 있는 필터를 확인하려면 [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) 저장 프로시저를 다음과 같이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-119">To identify the filters that are currently loaded on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) stored procedure, as follows:</span></span>  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 <span data-ttu-id="660d6-120">하지만 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 형식 이외의 다른 형식용 필터를 사용하려면 수동으로 서버 인스턴스에 로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="660d6-120">Before you can use filters for non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] formats, however, you must manually load them into the server instance.</span></span> <span data-ttu-id="660d6-121">추가 필터 설치에 대한 자세한 내용은 [등록된 필터와 단어 분리기 보기 및 변경](view-or-change-registered-filters-and-word-breakers.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="660d6-121">For information about installing additional filters, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
 <span data-ttu-id="660d6-122">**기존 전체 텍스트 인덱스의 유형 열을 보려면**</span><span class="sxs-lookup"><span data-stu-id="660d6-122">**To view the type column in an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="660d6-123">sys.fulltext_index_columns&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="660d6-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="660d6-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="660d6-124">See Also</span></span>  
 <span data-ttu-id="660d6-125">[fulltext_index_columns &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="660d6-125">[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span></span>  
 [<span data-ttu-id="660d6-126">FILESTREAM과 기타 SQL Server 기능 간 호환성</span><span class="sxs-lookup"><span data-stu-id="660d6-126">FILESTREAM Compatibility with Other SQL Server Features</span></span>](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
