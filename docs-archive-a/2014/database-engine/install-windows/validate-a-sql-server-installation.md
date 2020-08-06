---
title: SQL Server 설치 유효성 검사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730883"
---
# <a name="validate-a-sql-server-installation"></a><span data-ttu-id="6a89a-102">SQL Server 설치 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="6a89a-102">Validate a SQL Server Installation</span></span>
  <span data-ttu-id="6a89a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 검색 보고서를 사용하여 컴퓨터에 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 버전 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report can be used to verify the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features installed on the computer.</span></span> <span data-ttu-id="6a89a-104">**설치 된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 검색 보고서** 에는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 로컬 서버에 설치 된 모든,,,, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 및 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 제품 및 기능에 대 한 보고서가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-104">The **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report** displays a report of all [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] products and features that are installed on the local server.</span></span> <span data-ttu-id="6a89a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 검색 보고서는 **설치 센터의** 도구 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 페이지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report is available on the **Tools** page on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center.</span></span>  
  
 <span data-ttu-id="6a89a-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 검색 보고서를 실행하려면**</span><span class="sxs-lookup"><span data-stu-id="6a89a-106">**To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report:**</span></span>  
  
 <span data-ttu-id="6a89a-107">**시작** 메뉴를 사용하여 **모든 프로그램**, **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>** , **구성 도구**를 차례로 가리킨 다음 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터**를 클릭하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-107">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center, using the **Start** menu, point to **All Programs**, point to **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>**, point to **Configuration Tools**, and click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**.</span></span> <span data-ttu-id="6a89a-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 검색 보고서를 실행하려면 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 센터**의 왼쪽 탐색 영역에서 **도구**를 클릭한 다음 **설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능 검색 보고서**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-108">To run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report, click **Tools** in the left-hand navigation area of **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**, and then click **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report**.</span></span>  
  
 <span data-ttu-id="6a89a-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]검색 보고서 는% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<마지막 설치 세션 \> 에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report is saved to %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
 <span data-ttu-id="6a89a-110">명령줄을 통해 검색 보고서를 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a89a-110">You can also generate the discovery report through the command line.</span></span> <span data-ttu-id="6a89a-111">명령 프롬프트에서 "Setup.exe/Action = rundiscovery"를 실행 합니다. 위의 명령줄에 "/q"를 추가 하면 UI가 표시 되지 않지만 보고서 는% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<마지막 설치 세션에서 계속 생성 됩니다 \> .</span><span class="sxs-lookup"><span data-stu-id="6a89a-111">Run "Setup.exe /Action=RunDiscovery" from a command prompt If you add "/q" to the command line above no UI will be shown, but the report will still be created in %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a89a-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a89a-112">See Also</span></span>  
 [<span data-ttu-id="6a89a-113">SQL Server 설치 로그 파일 보기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="6a89a-113">View and Read SQL Server Setup Log Files</span></span>](view-and-read-sql-server-setup-log-files.md)  
  
  
