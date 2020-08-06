---
title: 스키마 캐싱 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e36711955fa28bafd3b0996b1a02f6cd71f3c4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659886"
---
# <a name="schema-caching-sqlxml-40"></a><span data-ttu-id="ec7ff-102">스키마 캐싱(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="ec7ff-102">Schema Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="ec7ff-103">Microsoft SQL Server 2000용 XML 웹 릴리스 1, Microsoft SQLXML 2.0 및 SQLXML 3.0을 함께 설치한 경우 다음 레지스트리 키를 사용하여 모든 버전에서 스키마 캐싱을 명시적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-103">With a side-by-side installation of XML for Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0, and SQLXML 3.0, you can explicitly control the schema caching in all versions by using the following registry keys:</span></span>  
  
 <span data-ttu-id="ec7ff-104">웹 릴리스 1:</span><span class="sxs-lookup"><span data-stu-id="ec7ff-104">Web Release 1:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 <span data-ttu-id="ec7ff-105">SQLXML 2.0:</span><span class="sxs-lookup"><span data-stu-id="ec7ff-105">SQLXML 2.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 <span data-ttu-id="ec7ff-106">SQLXML 3.0:</span><span class="sxs-lookup"><span data-stu-id="ec7ff-106">SQLXML 3.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="ec7ff-107">함께 설치 하는 방법에 대 한 자세한 내용은 [SQLXML 4.0 s p 1의 새로운 기능](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-107">For more information about side-by-side installation, see [What's New in SQLXML 4.0 SP1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).</span></span>  
  
 <span data-ttu-id="ec7ff-108">스키마 캐싱은 XPath 쿼리의 성능을 크게 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-108">Schema caching significantly improves the performance of an XPath query.</span></span> <span data-ttu-id="ec7ff-109">매핑 스키마에 대해 XPath 쿼리를 실행하면 스키마가 메모리에 저장되고 필요한 데이터 구조가 메모리에 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-109">When an XPath query is executed against a mapping schema, the schema is stored in memory, and the necessary data structures are built in memory.</span></span> <span data-ttu-id="ec7ff-110">스키마 캐싱이 설정되면 스키마가 메모리에 유지되므로 후속 XPath 쿼리의 성능이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-110">If schema caching is set, the schema remains in memory, thereby improving performance for subsequent XPath queries.</span></span>  
  
 <span data-ttu-id="ec7ff-111">스키마 캐시 크기를 설정하려면 레지스트리에 위의 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-111">You can set the schema cache size by adding the above key in the registry</span></span>  
  
 <span data-ttu-id="ec7ff-112">스키마 크기는 사용 가능한 메모리와 사용 중인 스키마 개수에 따라 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-112">The schema size is set based on the available memory and the number of schemas you are using.</span></span> <span data-ttu-id="ec7ff-113">기본 **SchemaCacheSize** 크기는 31입니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-113">The default **SchemaCacheSize** size is 31.</span></span> <span data-ttu-id="ec7ff-114">**SchemaCacheSize** 를 높게 설정 하면 더 많은 메모리가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-114">If you set **SchemaCacheSize** higher, more memory is used.</span></span> <span data-ttu-id="ec7ff-115">따라서 스키마 액세스 속도가 느리면 캐시 크기를 늘리고 메모리가 부족하면 캐시 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-115">Therefore, you can increase the cache size if schema access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="ec7ff-116">성능상의 이유로, 일반적으로 사용 하는 매핑 스키마 수보다 **SchemaCacheSize** 을 높게 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-116">For performance reasons, it is recommended that you set **SchemaCacheSize** higher than the number of mapping schemas you usually use.</span></span> <span data-ttu-id="ec7ff-117">스키마 수가 늘어나면 **SchemaCacheSize** 가 보유 한 스키마 수보다 적으면 성능이 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-117">As the number of schemas increase, if **SchemaCacheSize** is less than the number of schemas you have, the performance degrades.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ec7ff-118">스키마를 변경하더라도 2분 여 동안은 캐시에 반영되지 않으므로 개발 중에는 스키마를 캐싱하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ec7ff-118">During development, it is recommended that you do not cache the schemas, because the changes to the schemas are not reflected in the cache for about two minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec7ff-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec7ff-119">See Also</span></span>  
 <span data-ttu-id="ec7ff-120">[템플릿 캐싱은 SQLXML 4.0을 &#40;&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="ec7ff-120">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="ec7ff-121">&#40;SQLXML 4.0&#41;XSL 캐싱</span><span class="sxs-lookup"><span data-stu-id="ec7ff-121">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
