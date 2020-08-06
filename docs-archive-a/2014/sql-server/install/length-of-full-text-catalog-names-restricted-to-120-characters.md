---
title: 전체 텍스트 카탈로그 이름의 길이는 120 자로 제한 됩니다. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: fa9b06fa6fe4acd79782c19a8814357721e59c24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661498"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a><span data-ttu-id="f33c4-102">전체 텍스트 카탈로그 이름의 길이는 120자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33c4-102">Length of full-text catalog names restricted to 120 characters</span></span>
  <span data-ttu-id="f33c4-103">이전 릴리스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 128자였던 전체 텍스트 카탈로그 이름 길이가 모두 120자로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33c4-103">The length of full-text catalog names is restricted to 120 characters, reduced from the 128 character restriction in previous releases of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="description"></a><span data-ttu-id="f33c4-104">Description</span><span class="sxs-lookup"><span data-stu-id="f33c4-104">Description</span></span>  
 <span data-ttu-id="f33c4-105">이 변경 사항은 기존 카탈로그 이름에는 영향을 주지 않지만 이름이 120자보다 긴 전체 텍스트 카탈로그를 만드는 스크립트를 실행하면 오류가 발생하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f33c4-105">This change does not affect existing catalog names; however, scripts that create full-text catalogs with names longer than 120 characters result in an error.</span></span> <span data-ttu-id="f33c4-106">카탈로그 이름은 카탈로그에 해당하는 논리적 파일 이름을 생성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f33c4-106">The catalog names are used to generate logical file names that correspond to catalogs.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="f33c4-107">수정 동작</span><span class="sxs-lookup"><span data-stu-id="f33c4-107">Corrective Action</span></span>  
 <span data-ttu-id="f33c4-108">카탈로그 이름을 120자로 제한하도록 전체 텍스트 카탈로그를 만드는 모든 스크립트를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="f33c4-108">Modify all scripts that create full-text catalogs to ensure that they restrict catalog names to 120 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f33c4-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f33c4-109">See Also</span></span>  
 [<span data-ttu-id="f33c4-110">업그레이드 관리자 작업</span><span class="sxs-lookup"><span data-stu-id="f33c4-110">Working with Upgrade Advisor</span></span>](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
