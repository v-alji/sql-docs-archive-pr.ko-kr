---
title: 테이블 형식 모드로 Analysis Services 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729924"
---
# <a name="install-analysis-services-in-tabular-mode"></a><span data-ttu-id="15521-102">테이블 형식 모드에서 Analysis Services 설치</span><span class="sxs-lookup"><span data-stu-id="15521-102">Install Analysis Services in Tabular Mode</span></span>
  <span data-ttu-id="15521-103">새로운 테이블 형식 모델링 기능을 사용하기 위해 Analysis Services를 설치하는 경우 모델 유형을 지원하는 서버 모드에서 Analysis Services를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-103">If you are installing Analysis Services to use the new tabular modeling features, you must install Analysis Services in a server mode that supports that type of model.</span></span> <span data-ttu-id="15521-104">서버 모드는 테이블 형식이고 설치 동안 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="15521-104">The server mode is Tabular, and it is configured during installation.</span></span>  
  
 <span data-ttu-id="15521-105">이 모드로 서버를 설치한 이후에 테이블 형식 모델 디자이너에서 작성하는 호스트 솔루션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15521-105">After you install the server in this mode, you can use it host solutions that you build in tabular model designer.</span></span> <span data-ttu-id="15521-106">네트워크를 통해 테이블 형식 모델 데이터에 액세스하려는 경우 테이블 형식 모드 서버가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-106">A tabular mode server is required if you want tabular model data access over the network.</span></span>  
  
 <span data-ttu-id="15521-107">설치 마법사에서 또는 명령줄 설치에서 테이블 형식 모드를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15521-107">You can specify Tabular mode in the Installation Wizard or in a command line setup.</span></span> <span data-ttu-id="15521-108">다음 섹션에서는 각 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-108">The following sections describe each approach.</span></span>  
  
## <a name="installation-wizard"></a><span data-ttu-id="15521-109">설치 마법사</span><span class="sxs-lookup"><span data-stu-id="15521-109">Installation Wizard</span></span>  
 <span data-ttu-id="15521-110">다음 목록에서는 테이블 형식 모드의 Analysis Services를 설치하는 데 사용되는 SQL Server 설치 마법사의 해당 페이지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15521-110">The following list shows you which pages in the SQL Server Installation wizard are used to install Analysis Services in Tabular mode:</span></span>  
  
1.  <span data-ttu-id="15521-111">설치 프로그램의 기능 트리에서 **Analysis Services** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-111">Select **Analysis Services** from the Feature Tree in Setup.</span></span>  
  
     <span data-ttu-id="15521-112">![Analysis Services를 보여 주는 설치 기능 트리](../../../sql-server/install/media/ssas-setupas.gif "Analysis Services를 보여 주는 설치 기능 트리")</span><span class="sxs-lookup"><span data-stu-id="15521-112">![Setup feature tree showing Analsyis Services](../../../sql-server/install/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")</span></span>  
  
2.  <span data-ttu-id="15521-113">Analysis Services 구성 페이지에서 **테이블 형식 모드**를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-113">On the Analysis Services Configuration page, be sure to select **Tabular Mode**.</span></span>  
  
     <span data-ttu-id="15521-114">![Analysis Services 구성 옵션이 포함된 설치 페이지](../../../sql-server/install/media/ssas-setupasconfig.gif "Analysis Services 구성 옵션이 포함된 설치 페이지")</span><span class="sxs-lookup"><span data-stu-id="15521-114">![Setup page with Analysis Services config options](../../../sql-server/install/media/ssas-setupasconfig.gif "Setup page with Analysis Services config options")</span></span>  
  
 <span data-ttu-id="15521-115">테이블 형식 모드는 xVelocity 메모리 내 분석 엔진(VertiPaq)을 사용합니다. 이 엔진은 Analysis Services에 배포하는 테이블 형식 모델에 대한 기본 스토리지입니다.</span><span class="sxs-lookup"><span data-stu-id="15521-115">Tabular mode uses the xVelocity in-memory analytics engine (VertiPaq), which is the default storage for tabular models that you deploy to Analysis Services.</span></span> <span data-ttu-id="15521-116">테이블 형식 모델 솔루션을 서버에 배포한 이후에 테이블 형식 솔루션을 선택적으로 구성하여 메모리 집중형 스토리지 대신에 DirectQuery 디스크 스토리지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15521-116">After you deploy tabular model solutions to the server, you can selectively configure tabular solutions to use DirectQuery disk storage as an alternative to memory-bound storage.</span></span>  
  
## <a name="command-line-setup"></a><span data-ttu-id="15521-117">명령줄 설치</span><span class="sxs-lookup"><span data-stu-id="15521-117">Command Line Setup</span></span>  
 <span data-ttu-id="15521-118">SQL Server 설치에는 서버 모드를 지정하는 새로운 매개 변수(`ASSERVERMODE`)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="15521-118">SQL Server Setup includes a new parameter (`ASSERVERMODE`) that specifies the server mode.</span></span> <span data-ttu-id="15521-119">다음 예에서는 테이블 형식 서버 모드에 Analysis Services를 설치하는 명령줄 설치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15521-119">The following example illustrates a command line setup that installs Analysis Services in Tabular server mode.</span></span>  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="15521-120">`INSTANCENAME`은 17자 미만이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-120">`INSTANCENAME` must be less than 17 characters.</span></span>  
  
 <span data-ttu-id="15521-121">모든 자리 표시자 계정 값을 유효한 계정 및 암호로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-121">All placeholder account values must be replaced with valid accounts and password.</span></span>  
  
 <span data-ttu-id="15521-122">SQL Server Management Studio 또는 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 와 같은 도구는 제공되는 명령줄 구문 예를 사용하여 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15521-122">Tools such as SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] are not installed using the example command line syntax that is provided.</span></span> <span data-ttu-id="15521-123">기능을 추가 하는 방법에 대 한 자세한 내용은 [명령 프롬프트에서 SQL Server 2014 설치](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15521-123">For more information about adding features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
 <span data-ttu-id="15521-124">`ASSERVERMODE`는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-124">`ASSERVERMODE` is case-sensitive.</span></span>  <span data-ttu-id="15521-125">모든 값은 대문자로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-125">All values must be expressed in upper case.</span></span> <span data-ttu-id="15521-126">다음 표에는 `ASSERVERMODE`의 유효한 값에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15521-126">The following table describes the valid values for `ASSERVERMODE`.</span></span>  
  
|<span data-ttu-id="15521-127">값</span><span class="sxs-lookup"><span data-stu-id="15521-127">Value</span></span>|<span data-ttu-id="15521-128">Description</span><span class="sxs-lookup"><span data-stu-id="15521-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="15521-129">MULTIDIMENSIONAL</span><span class="sxs-lookup"><span data-stu-id="15521-129">MULTIDIMENSIONAL</span></span>|<span data-ttu-id="15521-130">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="15521-130">This is the default value.</span></span> <span data-ttu-id="15521-131">`ASSERVERMODE`를 설정하지 않은 경우 서버는 다차원 서버 모드에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="15521-131">If you do not set `ASSERVERMODE`, the server is installed in Multidimensional server mode.</span></span>|  
|<span data-ttu-id="15521-132">POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="15521-132">POWERPIVOT</span></span>|<span data-ttu-id="15521-133">이 값은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="15521-133">This value is optional.</span></span> <span data-ttu-id="15521-134">실제로 `ROLE` 매개 변수를 설정한 경우 서버 모드는 자동으로 1로 설정되며 `ASSERVERMODE`를 SharePoint용 PowerPivot 설치에 대한 옵션으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="15521-134">In practice, if you set the `ROLE` parameter, the server mode is automatically set to 1, making `ASSERVERMODE` optional for a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="15521-135">자세한 내용은 [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="15521-135">For more information, see [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).</span></span>|  
|<span data-ttu-id="15521-136">TABULAR</span><span class="sxs-lookup"><span data-stu-id="15521-136">TABULAR</span></span>|<span data-ttu-id="15521-137">명령줄 설치를 사용하여 테이블 형식 모드에 Analysis Services를 설치하는 경우 이 값이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="15521-137">This value is required if you are installing Analysis Services in Tabular mode using command line setup.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15521-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15521-138">See Also</span></span>  
 <span data-ttu-id="15521-139">[Analysis Services 인스턴스의 서버 모드 확인](../determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="15521-139">[Determine the Server Mode of an Analysis Services Instance](../determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="15521-140">[테이블 형식 모델 데이터베이스에 대 한 메모리 내 또는 DirectQuery 액세스 구성](../../tabular-models/enable-directquery-mode-in-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="15521-140">[Configure In-Memory or DirectQuery Access for a Tabular Model Database](../../tabular-models/enable-directquery-mode-in-ssms.md) </span></span>  
 [<span data-ttu-id="15521-141">테이블 형식 모델링 &#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="15521-141">Tabular Modeling &#40;SSAS Tabular&#41;</span></span>](../../tabular-models/tabular-models-ssas.md)  
  
  
