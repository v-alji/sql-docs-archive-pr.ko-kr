---
title: 템플릿, XSL 및 스키마 캐싱 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: rothja
ms.author: jroth
ms.openlocfilehash: 4df25909cf156957908abf0691964fd66a76343a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652034"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a><span data-ttu-id="84055-102">템플릿, XSL 및 스키마 캐싱(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="84055-102">Caching Templates, XSL, and Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="84055-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0은 성능 개선을 위해 템플릿, XSL 및 스키마 캐싱을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="84055-103">To improve performance, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supports caching templates, XSL, and schemas.</span></span>  
  
 <span data-ttu-id="84055-104">모든 스키마, 템플릿 및 XSL 파일(http:// 또는 ftp:// 위치의 파일 제외)이 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="84055-104">All schemas, templates, and XSL files (except the files from an http:// or ftp:// location) are cached.</span></span> <span data-ttu-id="84055-105">캐시된 파일은 프로세스가 실행되는 동안 메모리에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="84055-105">The cached files remain in memory while the process is running.</span></span> <span data-ttu-id="84055-106">프로세스가 종료되면 모든 캐시가 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="84055-106">As the process exits, all the cache is lost.</span></span> <span data-ttu-id="84055-107">따라서 쿼리당 한 프로세스를 실행하는 경우 캐시의 장점을 느끼지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="84055-107">Therefore, if you run one process per query, the caching benefit may not be noticeable.</span></span>  
  
 <span data-ttu-id="84055-108">이 섹션의 항목에서는 캐싱에 대한 자세한 내용을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84055-108">The topics in this section provide more information about caching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="84055-109">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="84055-109">In This Section</span></span>  
 [<span data-ttu-id="84055-110">템플릿 캐싱은 SQLXML 4.0을 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="84055-110">Template Caching &#40;SQLXML 4.0&#41;</span></span>](template-caching-sqlxml-4-0.md)  
 <span data-ttu-id="84055-111">템플릿 캐싱을 위한 레지스트리 키에 대해 설명하고 이를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84055-111">Describes and provides a registry key for template caching.</span></span>  
  
 [<span data-ttu-id="84055-112">&#40;SQLXML 4.0&#41;XSL 캐싱</span><span class="sxs-lookup"><span data-stu-id="84055-112">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
 <span data-ttu-id="84055-113">XSL 캐싱을 위한 레지스트리 키에 대해 설명하고 이를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84055-113">Describes and provides a registry key for XSL caching.</span></span>  
  
 [<span data-ttu-id="84055-114">스키마 캐싱은 SQLXML 4.0 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="84055-114">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
 <span data-ttu-id="84055-115">스키마 캐싱과 연관된 SQLXML 함께 설치 문제에 대해 설명하고 스키마 캐싱을 위한 레지스트리 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="84055-115">Discusses SQLXML side-by-side installation issues related to schema caching, and provides registry keys for schema caching.</span></span>  
  
  
