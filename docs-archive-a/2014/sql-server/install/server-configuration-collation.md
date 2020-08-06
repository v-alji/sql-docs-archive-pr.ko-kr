---
title: 서버 구성-데이터 정렬 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d06735590d23da6e91151202dd421639ea433b97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653126"
---
# <a name="server-configuration---collation"></a><span data-ttu-id="75de6-102">서버 구성 - 데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="75de6-102">Server Configuration - Collation</span></span>
  <span data-ttu-id="75de6-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 마법사의 서버 구성 - 데이터 정렬 페이지에서는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서 정렬하기 위해 사용하는 데이터 정렬 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-103">On the Server Configuration - Collation page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard, you can modify collation settings that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use for sorting purposes.</span></span> <span data-ttu-id="75de6-104">다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]설치나 다른 컴퓨터의 데이터 정렬 설정과 일치하는 옵션을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-104">Select the option to match collation settings of different installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or of another computer.</span></span>  
  
## <a name="options"></a><span data-ttu-id="75de6-105">옵션</span><span class="sxs-lookup"><span data-stu-id="75de6-105">Options</span></span>  
 <span data-ttu-id="75de6-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대해 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="75de6-106">Customize for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="75de6-107">에서는 Windows 데이터 정렬 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 정렬의 두 데이터 정렬 그룹을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-107">provides two groups of collations: Windows collations and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collations.</span></span> <span data-ttu-id="75de6-108">[!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에 대해 별도의 데이터 정렬 설정을 지정하거나 두 구성 요소에 대해 동일한 데이터 정렬을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-108">You can specify separate collation settings for the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or you can specify the same collation for both.</span></span>  
  
 <span data-ttu-id="75de6-109">기본적으로 미국 영어 시스템 로캘에 대해서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 정렬이 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-109">By default, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] collation is selected for US-English system locales.</span></span> <span data-ttu-id="75de6-110">지역화된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 대한 기본 데이터 정렬은 컴퓨터의 Windows 시스템 로캘 설정에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-110">The default collation for localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is determined by the Windows system locale setting for your computer.</span></span>  
  
 <span data-ttu-id="75de6-111">기본 설정은 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치의 데이터 정렬 설정이 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 사용하는 데이터 정렬 설정과 일치해야 하는 경우 또는 다른 컴퓨터의 Windows 시스템 로캘 설정과 일치해야 하는 경우에만 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-111">The default settings should be changed only if the collation setting for this installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must match the collation settings used by another instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or if it must match the Windows system locale of another computer.</span></span>  
  
 <span data-ttu-id="75de6-112">**참고** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 는 Windows 데이터 정렬만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-112">**Note** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses Windows collations only.</span></span> <span data-ttu-id="75de6-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 설치할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 과 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 간의 일관된 결과를 얻으려면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]를 설치하는 동안 Windows 데이터 정렬을 선택하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-113">If you plan to install [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], select a Windows collation during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to ensure consistent results between the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="75de6-114">자세한 내용은 [설치 프로그램에서 데이터 정렬 설정](https://go.microsoft.com/fwlink/?LinkId=190977)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-114">For more information, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="75de6-115">모범 사례</span><span class="sxs-lookup"><span data-stu-id="75de6-115">Best Practices</span></span>  
 <span data-ttu-id="75de6-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 프로그램에서 사용하는 Windows 시스템 로캘 및 해당 기본 데이터 정렬 표에 대한 자세한 내용은 [설치 프로그램에서 데이터 정렬 설정](https://go.microsoft.com/fwlink/?LinkId=190977)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-116">For more information about a table of Windows System locales and the corresponding default collations used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, see [Collation Settings in Setup](https://go.microsoft.com/fwlink/?LinkId=190977).</span></span>  
  
 <span data-ttu-id="75de6-117">가능한 경우 조직에 대해 단일 데이터 정렬을 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-117">If it is possible, use a single collation for your organization.</span></span> <span data-ttu-id="75de6-118">그러면 모든 데이터베이스, 열, 식 또는 식별자에 대해 명시적으로 데이터 정렬을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-118">This way, you do not have to explicitly specify the collation for every database, column, expression, or identifier.</span></span> <span data-ttu-id="75de6-119">여러 데이터 정렬과 코드 페이지 설정을 사용해야 할 경우 선행 정렬 우선 순위 규칙을 고려하도록 쿼리를 코딩하십시오.</span><span class="sxs-lookup"><span data-stu-id="75de6-119">If you must work with multiple collations and code page settings, code your queries to consider the rules of collation precedence.</span></span> <span data-ttu-id="75de6-120">자세한 내용은 온라인 설명서의 [선행 정렬&#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75de6-120">For more information, see the Books Online topic for [Collation Precedence &#40;Transact-SQL&#41;](/sql/t-sql/statements/collation-precedence-transact-sql).</span></span>  
  
 <span data-ttu-id="75de6-121">다음은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 데이터 정렬을 선택할 때 고려해야 할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-121">When you select a collation for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consider the following recommendations:</span></span>  
  
-   <span data-ttu-id="75de6-122">이진 코드 포인트 기반 정렬이 허용되는 경우 BINARY2 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-122">Select a BINARY2 collation if binary code point based ordering is acceptable.</span></span>  
  
-   <span data-ttu-id="75de6-123">데이터 형식 간 일관성 있는 비교를 원하는 경우 Windows 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-123">Select a Windows collation for consistent comparison across data types.</span></span>  
  
-   <span data-ttu-id="75de6-124">언어적 정렬에 대한 지원이 중요한 경우 새로운 100수준 데이터 정렬을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-124">Use a new 100-level collation for better linguistic sorting support.</span></span> <span data-ttu-id="75de6-125">자세한 내용은 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75de6-125">For more information, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
-   <span data-ttu-id="75de6-126">데이터베이스를 업그레이드된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스로 마이그레이션하려는 경우에는 기존 데이터베이스 데이터 정렬과 일치하는 데이터 정렬을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="75de6-126">If you plan to migrate a database to the upgraded instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], select the collation that matches your existing collation of the database.</span></span>  
  
  
