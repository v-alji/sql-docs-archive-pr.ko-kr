---
title: 명령 프롬프트에서 업그레이드 관리자 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- command prompt [Upgrade Advisor]
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: a6841cc2-ca13-4b1c-9343-9e4d54312c3a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: b0c5193f0b235b6d37170992d9d7ca9568b1f675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730044"
---
# <a name="installing-upgrade-advisor-from-the-command-prompt"></a><span data-ttu-id="694f8-102">명령 프롬프트에서 업그레이드 관리자 설치</span><span class="sxs-lookup"><span data-stu-id="694f8-102">Installing Upgrade Advisor from the Command Prompt</span></span>
  <span data-ttu-id="694f8-103">설치 마법사를 사용하거나 명령 프롬프트에서 업그레이드 관리자를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-103">You can install Upgrade Advisor either by using the Setup Wizard or from the command prompt.</span></span> <span data-ttu-id="694f8-104">명령 프롬프트를 사용하여 무인 및 자동 설치를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-104">By using the command prompt you can perform unattended and automated installations.</span></span>  
  
## <a name="installation-syntax"></a><span data-ttu-id="694f8-105">설치 구문</span><span class="sxs-lookup"><span data-stu-id="694f8-105">Installation Syntax</span></span>  
 <span data-ttu-id="694f8-106">명령 프롬프트에서 업그레이드 관리자를 설치하는 기본 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-106">The basic syntax for installing Upgrade Advisor from the command prompt is as follows:</span></span>  
  
 `SQLUA.msi [options]`  
  
 <span data-ttu-id="694f8-107">다음 표에서는 가장 일반적인 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-107">The following table shows the most common options.</span></span>  
  
|<span data-ttu-id="694f8-108">인수</span><span class="sxs-lookup"><span data-stu-id="694f8-108">Argument</span></span>|<span data-ttu-id="694f8-109">Description</span><span class="sxs-lookup"><span data-stu-id="694f8-109">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="694f8-110">/q [n&#124;b&#124;r&#124;f]</span><span class="sxs-lookup"><span data-stu-id="694f8-110">/q[n&#124;b&#124;r&#124;f]</span></span>|<span data-ttu-id="694f8-111">다음과 같이 UI(사용자 인터페이스) 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-111">Sets user interface (UI) level:</span></span><br /><br /> <span data-ttu-id="694f8-112">n = UI 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="694f8-112">n = no UI</span></span><br /><br /> <span data-ttu-id="694f8-113">b = 기본 UI(진행률만 표시하고 프롬프트는 표시 안 함)</span><span class="sxs-lookup"><span data-stu-id="694f8-113">b = basic UI (progress only, no prompts)</span></span><br /><br /> <span data-ttu-id="694f8-114">r = 축소된 UI(설치가 끝날 때 대화 상자 표시)</span><span class="sxs-lookup"><span data-stu-id="694f8-114">r = reduced UI (dialog box at the end of installation)</span></span><br /><br /> <span data-ttu-id="694f8-115">f = 전체 UI</span><span class="sxs-lookup"><span data-stu-id="694f8-115">f = full UI</span></span>|  
|<span data-ttu-id="694f8-116">/L</span><span class="sxs-lookup"><span data-stu-id="694f8-116">/L</span></span>|<span data-ttu-id="694f8-117">로그 파일 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-117">Specifies log file options.</span></span> <span data-ttu-id="694f8-118">*Log_file_name*에 모든 메시지를 기록 하려면 **-L \* v**_log_file_name_를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-118">To log all messages to *log_file_name*, use **-L\*v**_log_file_name_.</span></span> <span data-ttu-id="694f8-119">오류 메시지만 기록 하려면 log_file_name을 사용 `-Le` *log_file_name*합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-119">To log error messages only, use `-Le`*log_file_name*.</span></span>|  
|<span data-ttu-id="694f8-120">ADDLOCAL = ALL&#124; REMOVE = ALL&#124;REINSTALL = ALL</span><span class="sxs-lookup"><span data-stu-id="694f8-120">ADDLOCAL=ALL&#124; REMOVE=ALL&#124;REINSTALL=ALL</span></span>|<span data-ttu-id="694f8-121">업그레이드 관리자의 설치(ADDLOCAL), 제거(REMOVE) 또는 다시 설치(REINSTALL)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-121">Specifies to install (ADDLOCAL), remove (REMOVE), or reinstall (REINSTALL) Upgrade Advisor.</span></span>|  
|<span data-ttu-id="694f8-122">UAINSTALLDIR=path</span><span class="sxs-lookup"><span data-stu-id="694f8-122">UAINSTALLDIR=path</span></span>|<span data-ttu-id="694f8-123">경로를 사용하여 지정한 위치에 업그레이드 관리자를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-123">Installs Upgrade Advisor to the location specified by path.</span></span>|  
  
## <a name="installation-examples"></a><span data-ttu-id="694f8-124">설치 예</span><span class="sxs-lookup"><span data-stu-id="694f8-124">Installation Examples</span></span>  
 <span data-ttu-id="694f8-125">다음 예에서는 명령 프롬프트를 사용하여 업그레이드 관리자를 설치하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-125">The following example shows how to install Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="694f8-126">이 명령을 실행할 때는 다음과 같이 Msiexec 프로그램을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-126">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn ADDLOCAL=ALL UAINSTALLDIR="C:\Upgrade Advisor"  
```  
  
 <span data-ttu-id="694f8-127">이렇게 하면 추가 설치 옵션을 사용해야 하는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-127">This can be helpful if you have to use additional installation options.</span></span>  
  
## <a name="removal-examples"></a><span data-ttu-id="694f8-128">제거 예</span><span class="sxs-lookup"><span data-stu-id="694f8-128">Removal Examples</span></span>  
 <span data-ttu-id="694f8-129">다음 예에서는 명령 프롬프트를 사용하여 업그레이드 관리자를 제거하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-129">The following example shows how to remove Upgrade Advisor by using the command prompt:</span></span>  
  
```  
SQLUA.msi /qn REMOVE=ALL  
```  
  
 <span data-ttu-id="694f8-130">이 명령을 실행할 때는 다음과 같이 Msiexec 프로그램을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="694f8-130">You can also use the Msiexec program when you run this command:</span></span>  
  
```  
Msiexec.exe /i C:\Downloads\SQLUA.msi /qn REMOVE=ALL  
```  
  
## <a name="see-also"></a><span data-ttu-id="694f8-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="694f8-131">See Also</span></span>  
 <span data-ttu-id="694f8-132">[업그레이드 관리자 설치](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="694f8-132">[Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="694f8-133">업그레이드 관리자 필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="694f8-133">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
