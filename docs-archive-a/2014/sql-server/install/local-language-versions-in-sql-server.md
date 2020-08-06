---
title: SQL Server의 로컬 언어 버전 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 20b99363-0490-4aa3-9a3d-262f827d81e8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646ffaed1e4b709c2c26030379f0a7f223f221e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730036"
---
# <a name="local-language-versions-in-sql-server"></a><span data-ttu-id="15482-102">SQL Server의 로컬 언어 버전</span><span class="sxs-lookup"><span data-stu-id="15482-102">Local Language Versions in SQL Server</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="15482-103">에서는 Windows 운영 체제에서 지원하는 모든 언어를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-103">supports all languages that are supported by Windows operating systems.</span></span>  
  
## <a name="cross-language-support"></a><span data-ttu-id="15482-104">언어 간 호환성 지원</span><span class="sxs-lookup"><span data-stu-id="15482-104">Cross-Language Support</span></span>  
  
-   <span data-ttu-id="15482-105">영어 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 지역화된 모든 운영 체제에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="15482-105">The English-language version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is supported on all localized versions of operating systems.</span></span>  
  
-   <span data-ttu-id="15482-106">지역화된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 해당 언어를 사용하는 지역화된 운영 체제에서는 물론 Windows MUI(Multilingual User Interface) Pack 설정을 사용하여 영어 버전의 운영 체제에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="15482-106">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on localized operating systems with the corresponding language or on English-language versions of supported operating systems by using the Windows Multilingual User Interface Pack (MUI) settings.</span></span> <span data-ttu-id="15482-107">자세한 내용은 [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15482-107">For more information, see [Configure Operating System to Support Localized Versions](../../../2014/sql-server/install/local-language-versions-in-sql-server.md#BK_ConfigureOS).</span></span>  
  
-   <span data-ttu-id="15482-108">지역화된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 같은 언어로 지역화된 버전으로만 업그레이드할 수 있으며 영어 버전으로는 업그레이드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-108">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can only be upgraded to localized versions of the same language, and cannot be upgraded to the English-language version.</span></span>  
  
-   <span data-ttu-id="15482-109">지역화된 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 영어 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스와 함께 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-109">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can also be installed side by side with English-language instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
##  <a name="configure-operating-system-to-support-localized-versions"></a><a name="BK_ConfigureOS"></a> <span data-ttu-id="15482-110">Configure Operating System to Support Localized Versions</span><span class="sxs-lookup"><span data-stu-id="15482-110">Configure Operating System to Support Localized Versions</span></span>  
 <span data-ttu-id="15482-111">Windows MUI(Multilingual User Interface Pack) 설정을 사용하면 지원되는 운영 체제의 영어 버전에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 해당 언어 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-111">Localized versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are supported on English-language versions of supported operating systems through the use of Windows Multilingual User Interface Pack (MUI) settings.</span></span>  
  
 <span data-ttu-id="15482-112">그러나 영어 이외의 MUI 설정을 포함하는 영어 운영 체제가 실행되는 서버에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 해당 언어 버전을 설치하기 전에 특정 운영 체제 설정을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-112">However, you must verify certain operating system settings before installing a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a server that is running an English-language operating system with a non-English MUI setting.</span></span> <span data-ttu-id="15482-113">다음 운영 체제 설정이 설치할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 언어와 일치하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-113">You need to verify that the following operating system settings match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed:</span></span>  
  
-   <span data-ttu-id="15482-114">운영 체제 사용자 인터페이스 설정</span><span class="sxs-lookup"><span data-stu-id="15482-114">The operating system user interface setting</span></span>  
  
-   <span data-ttu-id="15482-115">운영 체제 사용자 로캘 설정</span><span class="sxs-lookup"><span data-stu-id="15482-115">The operating system user locale setting</span></span>  
  
-   <span data-ttu-id="15482-116">시스템 로캘 설정</span><span class="sxs-lookup"><span data-stu-id="15482-116">The system locale setting</span></span>  
  
 <span data-ttu-id="15482-117">설정이 설치할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 언어와 일치하지 않으면 다음 절차에 따라 이러한 운영 체제 설정을 올바르게 설정하십시오.</span><span class="sxs-lookup"><span data-stu-id="15482-117">If the settings do not match the language of the localized [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to be installed, then use the following procedures to correctly set these operating system settings.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="15482-118">동일한 컴퓨터에서 서로 다른 언어 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 설치는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-118">Installations of different language versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances on the same computer are not supported.</span></span>  
  
#### <a name="to-change-the-operating-system-user-interface-setting"></a><span data-ttu-id="15482-119">운영 체제 사용자 인터페이스 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="15482-119">To change the operating system user interface setting</span></span>  
  
1.  <span data-ttu-id="15482-120">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 해당 언어 버전과 일치하는 운영 체제 MUI를 아직 설치하지 않았으면 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-120">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="15482-121">제어판에서 **국가 및 언어 옵션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="15482-121">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="15482-122">**언어** 탭의 **메뉴 및 대화 상자에 사용된 언어**에서 목록의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-122">On the **Languages** tab, for **Language used in menus and dialogs**, select a value from the list.</span></span>  
  
     <span data-ttu-id="15482-123">이 설정은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 사용자 인터페이스 언어에 영향을 주므로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 해당 언어 버전과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-123">This setting will affect the user interface language of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], so it must match your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
4.  <span data-ttu-id="15482-124">**적용** 을 클릭하여 변경 내용을 확인하거나 **확인** 을 클릭하여 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-124">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-operating-system-user-locale-setting"></a><span data-ttu-id="15482-125">운영 체제 사용자 로캘 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="15482-125">To change the operating system user locale setting</span></span>  
  
1.  <span data-ttu-id="15482-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 해당 언어 버전과 일치하는 운영 체제 MUI를 아직 설치하지 않았으면 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-126">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="15482-127">제어판에서 **국가 및 언어 옵션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="15482-127">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="15482-128">**국가별 옵션** 탭의 **아래에서 원하는 항목을 선택하거나 [사용자 지정]을 클릭하여 필요한 형식을 만드십시오**에서 목록의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-128">On the **Regional Options** tab, for **Select an item to match its preferences**, select a value from the list.</span></span>  
  
     <span data-ttu-id="15482-129">이 설정은 culture별 데이터 서식에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15482-129">This setting will affect culture-specific data formatting.</span></span>  
  
4.  <span data-ttu-id="15482-130">**적용** 을 클릭하여 변경 내용을 확인하거나 **확인** 을 클릭하여 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-130">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
#### <a name="to-change-the-system-locale-setting"></a><span data-ttu-id="15482-131">시스템 로캘 설정을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="15482-131">To change the system locale setting</span></span>  
  
1.  <span data-ttu-id="15482-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 해당 언어 버전과 일치하는 운영 체제 MUI를 아직 설치하지 않았으면 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-132">If not already installed, install the operating system MUI that matches your localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="15482-133">제어판에서 **국가 및 언어 옵션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="15482-133">In Control Panel, open **Regional and Language Options**.</span></span>  
  
3.  <span data-ttu-id="15482-134">**고급** 탭의 **유니코드를 지원하지 않는 프로그램의 언어 버전과 일치하는 언어를 선택하십시오**에서 목록의 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15482-134">On the **Advanced** tab, for **Select a language to match the language version of the non-Unicode programs you want to use**, select a value from the list.</span></span>  
  
     <span data-ttu-id="15482-135">이 설정을 사용하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 중에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치에 대한 최상의 기본 데이터 정렬을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-135">This setting will allow [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup to choose the best default collation for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
4.  <span data-ttu-id="15482-136">**적용** 을 클릭하여 변경 내용을 확인하거나 **확인** 을 클릭하여 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="15482-136">Click **Apply** to confirm the change, and **OK** to close the window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15482-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15482-137">See Also</span></span>  
 <span data-ttu-id="15482-138">[SQL Server 2014를 설치 하기 위한 하드웨어 및 소프트웨어 요구 사항](hardware-and-software-requirements-for-installing-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15482-138">[Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md) </span></span>  
 [<span data-ttu-id="15482-139">SQL Server 2014 설치</span><span class="sxs-lookup"><span data-stu-id="15482-139">Install SQL Server 2014</span></span>](../../database-engine/install-windows/install-sql-server.md)  
  
  
