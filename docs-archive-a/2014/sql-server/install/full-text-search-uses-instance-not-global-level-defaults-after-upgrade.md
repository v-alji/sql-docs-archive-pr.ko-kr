---
title: 업그레이드 하면 전체 텍스트 검색에서 전역, 단어 분리기 및 필터를 기본적으로 사용 하는 인스턴스 수준을 사용 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0b6cea7ab63351fad25f0205a614e364328171a9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661507"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a><span data-ttu-id="6a2f8-102">업그레이드하면 기본적으로 전체 텍스트 Search에서 전역 수준이 아닌 인스턴스 수준의 단어 분리기와 필터를 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a2f8-102">Upgrading will cause Full-Text Search to use instance-level, not global, word breakers and filters by default</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6a2f8-103">에서는 새 단어 분리기와 필터를 인스턴스 수준에서 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a2f8-103">provides a way to allow instance-level registration of new word breakers and filters.</span></span>  
  
## <a name="component"></a><span data-ttu-id="6a2f8-104">구성 요소</span><span class="sxs-lookup"><span data-stu-id="6a2f8-104">Component</span></span>  
 <span data-ttu-id="6a2f8-105">전체 텍스트 검색</span><span class="sxs-lookup"><span data-stu-id="6a2f8-105">Full-Text Search</span></span>  
  
## <a name="description"></a><span data-ttu-id="6a2f8-106">Description</span><span class="sxs-lookup"><span data-stu-id="6a2f8-106">Description</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6a2f8-107">에서는 새 단어 분리기와 필터를 인스턴스 수준에서 등록할 수 있으므로</span><span class="sxs-lookup"><span data-stu-id="6a2f8-107">allows the instance-level registration of new word breakers and filters.</span></span> <span data-ttu-id="6a2f8-108">인스턴스 간에 기능과 보안이 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a2f8-108">This instance-level registration provides functional and security isolation between instances.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="6a2f8-109">수정 동작</span><span class="sxs-lookup"><span data-stu-id="6a2f8-109">Corrective Action</span></span>  
 <span data-ttu-id="6a2f8-110">업그레이드한 후 `sp_fulltext_service`를 사용하여 구성 요소를 로드할 수 있도록 서비스 속성 및 `load_os_resources`를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6a2f8-110">After upgrading, use the `sp_fulltext_service` to set the service property and `load_os_resources`, which allows the components to be loaded.</span></span> <span data-ttu-id="6a2f8-111">다음을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a2f8-111">You must run the following:</span></span>  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a><span data-ttu-id="6a2f8-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a2f8-112">See Also</span></span>  
 [<span data-ttu-id="6a2f8-113">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="6a2f8-113">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
