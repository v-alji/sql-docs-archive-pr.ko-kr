---
title: 데이터 원본에 연결 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndatasource.f1
ms.assetid: 1e2b17e9-092b-4af1-8a58-c52b8fe10ff1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4fe7f7d5b31118369b8ce2a855b955e44f661dbc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648025"
---
# <a name="connect-to-a-data-source-ssas"></a><span data-ttu-id="9cc37-102">데이터 원본에 연결(SSAS)</span><span class="sxs-lookup"><span data-stu-id="9cc37-102">Connect to a Data Source (SSAS)</span></span>
  <span data-ttu-id="9cc37-103">**테이블 가져오기 마법사** 의 이 페이지에서는 관계형 데이터베이스, 데이터 피드, 파일 등과 같은 다양한 데이터 원본을 대상으로 새 데이터 원본 연결을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-103">This page of the **Table Import Wizard** enables you to create a new data source connection to a variety of data sources, such as relational databases, data feeds, and files.</span></span> <span data-ttu-id="9cc37-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 마법사에 액세스하려면 **모델** 메뉴에서 **데이터 원본에서 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="9cc37-105">데이터 원본에 연결하려면 컴퓨터에 적절한 공급자가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-105">To connect to a data source, you must have the appropriate provider installed on your machine.</span></span> <span data-ttu-id="9cc37-106">작업 영역 데이터베이스 서버에도 적절한 공급자가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-106">You must also have the appropriate provider installed on the workspace database server.</span></span> <span data-ttu-id="9cc37-107">32비트(x86) 서버의 경우 32비트 공급자가 설치되어 있어야 하며</span><span class="sxs-lookup"><span data-stu-id="9cc37-107">For 32-bit (x86) servers, 32-bit providers must be installed.</span></span> <span data-ttu-id="9cc37-108">64비트(x64) 서버의 경우 64비트 공급자가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-108">For 64-bit (x64) servers, 64-bit providers must be installed.</span></span>  
  
 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]<span data-ttu-id="9cc37-109">는 아키텍처에 관계없이 항상 32비트 프로세스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-109">always runs in a 32-bit process, regardless of architecture.</span></span> <span data-ttu-id="9cc37-110">64비트 컴퓨터에서 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 를 실행하는 경우 데이터 공급자를 설치할 때 다음 사항에 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-110">When running [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] on a 64-bit machine, you should be aware of the following when installing data providers:</span></span>  
  
-   <span data-ttu-id="9cc37-111">32비트와 64비트 공급자를 함께 설치할 수 있는 공급자의 경우 두 공급자를 모두 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-111">For providers that support side-by-side installation of 32-bit and 64-bit providers, you should install both providers.</span></span>  
  
-   <span data-ttu-id="9cc37-112">ACE 공급자의 경우 64비트 버전의 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-112">For the ACE provider, you must install the 64-bit version of the provider.</span></span> <span data-ttu-id="9cc37-113">Office에서는 ACE 공급자가 자동으로 설치되므로 작업 영역 데이터베이스 서버를 호스팅하는 64비트 컴퓨터에서 32비트 버전의 Microsoft Office를 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-113">Because Office automatically installs the ACE provider, you should not run a 32-bit version of Microsoft Office on a 64-bit machine hosting the workspace database server.</span></span>  
  
     <span data-ttu-id="9cc37-114">ACE 공급자는 텍스트, Excel 및 Access 파일에서 가져오기 작업을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-114">The ACE provider is used to import from Text, Excel, and Access files.</span></span> <span data-ttu-id="9cc37-115">이러한 데이터 원본에 대한 지원이 필요하지 않은 경우 64비트 작업 영역 데이터베이스 서버를 실행하는 컴퓨터에서 32비트 버전의 Microsoft Office를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-115">If support for these data sources is not needed, you can then run a 32-bit version of Microsoft Office on a machine running a 64-bit workspace database server.</span></span>  
  
-   <span data-ttu-id="9cc37-116">32비트와 64비트 공급자를 함께 설치할 수 없는 기타 공급자의 경우에는 32비트 공급자를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-116">For other providers that do not support side-by-side installation of 32-bit and 64-bit providers, you must install the 32-bit provider.</span></span> <span data-ttu-id="9cc37-117">64비트 컴퓨터만 사용할 수 있는 경우 64비트 공급자가 설치된 원격 컴퓨터를 작업 영역 데이터베이스 서버로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cc37-117">If only 64-bit machines are available, you must use a remote machine with a 64-bit provider installed as the workspace database server.</span></span>  
  
  
