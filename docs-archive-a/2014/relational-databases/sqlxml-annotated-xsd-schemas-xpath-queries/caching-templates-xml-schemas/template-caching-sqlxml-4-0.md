---
title: 템플릿 캐싱 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: rothja
ms.author: jroth
ms.openlocfilehash: b2ea8a539086ada1b15abbb9cff4f838af45818c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650876"
---
# <a name="template-caching-sqlxml-40"></a><span data-ttu-id="a8975-102">템플릿 캐싱(SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a8975-102">Template Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="a8975-103">템플릿 캐싱은 성능을 크게 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-103">Template caching significantly improves performance.</span></span> <span data-ttu-id="a8975-104">템플릿 캐싱이 설정되어 있으면 템플릿이 처음 실행될 때 메모리에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-104">If template caching is set, the template remains in memory upon its first execution.</span></span> <span data-ttu-id="a8975-105">따라서 후속 템플릿 실행 성능이 개선됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-105">This improves the performance for the subsequent execution of the template.</span></span>  
  
 <span data-ttu-id="a8975-106">템플릿 캐시 크기를 설정하려면 레지스트리에 다음 키를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-106">You can set the template cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="a8975-107">템플릿 크기는 사용 가능한 메모리와 사용 중인 템플릿 개수에 따라 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-107">The template size should be set on the basis of the available memory and the number of templates you are using.</span></span> <span data-ttu-id="a8975-108">**Templatecachesize** 크기의 기본값은 31입니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-108">The default of **TemplateCacheSize** size is 31.</span></span> <span data-ttu-id="a8975-109">템플릿 액세스 속도가 느리다고 생각되면 캐시 크기를 늘리고, 메모리가 부족하면 캐시 크기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-109">You can increase the cache size if template access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="a8975-110">성능을 향상 시키려면 일반적으로 사용 하는 템플릿 수보다 많은 **Templatecachesize** 를 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-110">For better performance, it is recommended that you set **TemplateCacheSize** higher than the number of templates you usually use.</span></span> <span data-ttu-id="a8975-111">**TemlateCacheSize** 가 템플릿 수보다 적으면 템플릿 수가 증가 하면 성능이 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-111">If **TemlateCacheSize** is less than the number of templates you have, performance degrades as the number of templates increase.</span></span> <span data-ttu-id="a8975-112">**Templatecachesize** 를 최대 128로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-112">The **TemplateCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="a8975-113">캐시된 템플릿이 사용될 때마다 템플릿을 새로 고쳐야 하는지 확인하기 위해 템플릿 파일의 수정 시간이 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-113">Every time a cached template is used, the modification time of the template file is checked to see whether it needs to be refreshed.</span></span> <span data-ttu-id="a8975-114">왜냐하면 캐시 복사본보다 디스크 복사본이 최신이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8975-115">템플릿 매개 변수와 명령 속성은 캐시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8975-115">Template parameters and command properties are not cached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8975-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8975-116">See Also</span></span>  
 <span data-ttu-id="a8975-117">[스키마 캐싱은 SQLXML 4.0 &#40;&#41;](schema-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="a8975-117">[Schema Caching &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="a8975-118">&#40;SQLXML 4.0&#41;XSL 캐싱</span><span class="sxs-lookup"><span data-stu-id="a8975-118">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
