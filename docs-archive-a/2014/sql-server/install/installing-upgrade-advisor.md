---
title: 업그레이드 관리자 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730047"
---
# <a name="installing-upgrade-advisor"></a><span data-ttu-id="368d6-102">업그레이드 관리자 설치</span><span class="sxs-lookup"><span data-stu-id="368d6-102">Installing Upgrade Advisor</span></span>
  <span data-ttu-id="368d6-103">SQL Server 2014 업그레이드 관리자 설치 위치는 분석 대상에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-103">Where you install SQL Server 2014 Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="368d6-104">업그레이드 관리자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 제외하고 모든 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 구성 요소의 원격 분석을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-104">Upgrade Advisor supports remote analysis of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="368d6-105">인스턴스를 검색 하지 않는 경우 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 에 연결할 수 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있고 [업그레이드 관리자의 필수 구성 요소](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)를 충족 하는 모든 컴퓨터에 업그레이드 관리자를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-105">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the [Upgrade Advisor Prerequisites](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md).</span></span> <span data-ttu-id="368d6-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 인스턴스를 검색하는 경우에는 보고서 서버에 업그레이드 관리자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="368d6-107">**SQLUA.msi** 파일을 실행 하 여 업그레이드 관리자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-107">Run the **SQLUA.msi** file to install Upgrade Advisor.</span></span> <span data-ttu-id="368d6-108">명령 프롬프트를 사용하여 무인 및 자동 설치를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-108">You can install from the command prompt for unattended and automated installations.</span></span> <span data-ttu-id="368d6-109">구문 및 예제 [는 명령 프롬프트에서 업그레이드 관리자 설치를](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="368d6-109">See [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) for syntax and examples.</span></span>  
  
 <span data-ttu-id="368d6-110">SQLUA.msi를</span><span class="sxs-lookup"><span data-stu-id="368d6-110">Get SQLUA.msi:</span></span>  
  
-   <span data-ttu-id="368d6-111">제품 미디어의 **redist** 폴더에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 있습니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-111">In the **redist** folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product media.</span></span>  
  
-   <span data-ttu-id="368d6-112">[SQL 2014 기능 팩 다운로드](https://www.microsoft.com/download/details.aspx?id=42295)의 일부로 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-112">As part of the [SQL 2014 Feature Pack download](https://www.microsoft.com/download/details.aspx?id=42295).</span></span>  
  
## <a name="uninstalling-upgrade-advisor"></a><span data-ttu-id="368d6-113">업그레이드 관리자 제거</span><span class="sxs-lookup"><span data-stu-id="368d6-113">Uninstalling Upgrade Advisor</span></span>  
 <span data-ttu-id="368d6-114">**프로그램 추가/제거**를 사용 하 여 업그레이드 관리자를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-114">You can uninstall Upgrade Advisor by using **Add or Remove Programs**.</span></span> <span data-ttu-id="368d6-115">명령 프롬프트 구문도 제거/설치 제거를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="368d6-115">The command prompt syntax also supports removal/uninstall.</span></span>  
  
  
