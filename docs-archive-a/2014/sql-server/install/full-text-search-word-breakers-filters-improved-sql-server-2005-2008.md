---
title: SQL Server 2005 및 SQL Server 2008에서 전체 텍스트 검색 단어 분리기와 필터가 크게 향상 되었습니다. Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 8d06bda9-0bbf-4baa-b270-07b1c1f640eb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d2e7d3b8da56b407d3937b05cd980c3f8a4eb0c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660318"
---
# <a name="full-text-search-word-breakers-and-filters-significantly-improved-in-sql-server-2005-and-sql-server-2008"></a><span data-ttu-id="6a226-102">SQL Server 2005와 SQL Server 2008에서는 전체 텍스트 Search 단어 분리기와 필터가 크게 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-102">Full-Text Search word breakers and filters significantly improved in SQL Server 2005 and SQL Server 2008</span></span>
  <span data-ttu-id="6a226-103">단어 분리기와 필터가 대폭 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-103">The word breakers and filters were significantly changed.</span></span> <span data-ttu-id="6a226-104">언어 범위와 안정성을 포함하여 단어 분리기의 기능이 추가로 개선되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-104">Additional improvements have been made to word breakers, including enhanced language coverage and reliability.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6a226-105">Description</span><span class="sxs-lookup"><span data-stu-id="6a226-105">Description</span></span>  
 <span data-ttu-id="6a226-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 검색에서 사용하는 단어 분리기와 필터가 대폭 수정되어 기능 및 안정성이 개선되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-106">Word breakers and filters used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Full-Text Search have been significantly modified to achieve improvements in functionality and reliability.</span></span> <span data-ttu-id="6a226-107">일부 특수한 경우 단어 분리기의 변경은 데이터를 토큰화하는 방식에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-107">In some specific cases, changes to the word breakers can impact how some data is tokenized.</span></span> <span data-ttu-id="6a226-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]에서 만든 토큰은 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 또는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 만든 이전 토큰과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a226-108">Tokens created in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] may be different from earlier tokens created in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] or [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="6a226-109">단어 분리기에 대 한 자세한 내용은 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6a226-109">For information about word breakers, see [Configure and Manage Word Breakers and Stemmers for Search](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a226-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a226-110">See Also</span></span>  
 [<span data-ttu-id="6a226-111">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="6a226-111">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
