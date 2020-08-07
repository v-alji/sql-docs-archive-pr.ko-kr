---
title: XSL 캐싱 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: rothja
ms.author: jroth
ms.openlocfilehash: e41f247c34c1b40bedfdf6924a45afe5f63735b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732484"
---
# <a name="xsl-caching-sqlxml-40"></a><span data-ttu-id="af103-102">XSL 캐싱(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="af103-102">XSL Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="af103-103">XSL 스타일시트를 캐시하면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="af103-103">Caching XSL style sheets improves performance.</span></span> <span data-ttu-id="af103-104">XSL 스타일시트를 처음 캐시할 때 XSL 캐싱이 ON으로 설정되어 있으면 XSL 스타일시트가 메모리에 유지되므로 후속 처리의 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="af103-104">Upon its first execution, an XSL style sheet remains in memory if XSL caching is set to ON; this improves performance for subsequent processing.</span></span> <span data-ttu-id="af103-105">기본 설정은 ON입니다.</span><span class="sxs-lookup"><span data-stu-id="af103-105">The default setting is ON.</span></span>  
  
 <span data-ttu-id="af103-106">XSL 캐시 크기를 설정하려면 레지스트리에 다음 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="af103-106">You can set the XSL cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="af103-107">XSL 캐시 크기는 사용 가능한 메모리와 사용 중인 XSL 스타일시트의 개수에 따라 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af103-107">The XSL cache size should be set on the basis of the available memory and the number of XSL style sheets you are using.</span></span> <span data-ttu-id="af103-108">**XSLCacheSize** 크기의 기본값은 31입니다.</span><span class="sxs-lookup"><span data-stu-id="af103-108">The default of **XSLCacheSize** size is 31.</span></span> <span data-ttu-id="af103-109">XSL 액세스 속도가 느리다고 생각되면 캐시 크기를 늘리고, 메모리가 부족하면 캐시 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af103-109">You can increase the cache size if XSL access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="af103-110">성능을 더 높이려면 **XSLCacheSize** 를 일반적으로 사용하는 XSL 스타일시트의 개수보다 크게 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="af103-110">For better performance, it is recommended that you set **XSLCacheSize** higher than the number of XSL style sheets you usually use.</span></span> <span data-ttu-id="af103-111">**XSLCacheSize** 가 사용 중인 XSL 스타일시트의 개수보다 작으면 XSL 스타일시트 개수가 늘어나면서 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="af103-111">If **XSLCacheSize** is less than the number of XSL style sheets you have, the performance degrades as the number of XSL style sheets increases.</span></span> <span data-ttu-id="af103-112">**XSLCacheSize** 는 최대 128까지 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af103-112">The **XSLCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="af103-113">캐시된 XSL 스타일시트가 사용될 때마다 XSL 파일을 새로 고쳐야 하는지 확인하기 위해 템플릿 파일의 수정 시간이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="af103-113">Every time the cached XSL style sheet is used, the modification time of the XSL file is checked to determine whether it needs to be refreshed.</span></span> <span data-ttu-id="af103-114">왜냐하면 캐시 복사본보다 디스크 복사본이 최신이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="af103-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af103-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af103-115">See Also</span></span>  
 <span data-ttu-id="af103-116">[템플릿 캐싱은 SQLXML 4.0을 &#40;&#41;](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="af103-116">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="af103-117">스키마 캐싱은 SQLXML 4.0 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="af103-117">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
  
  
