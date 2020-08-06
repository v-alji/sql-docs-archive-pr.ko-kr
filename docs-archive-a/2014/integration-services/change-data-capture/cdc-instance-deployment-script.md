---
title: CDC 인스턴스 배포 스크립트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8fa82822-ac99-48ef-a18d-f4f3a77105b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6deea884168c2329e312eeaa2be16c28a955cca3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741199"
---
# <a name="cdc-instance-deployment-script"></a><span data-ttu-id="bbc32-102">CDC 인스턴스 배포 스크립트</span><span class="sxs-lookup"><span data-stu-id="bbc32-102">CDC Instance Deployment Script</span></span>
  <span data-ttu-id="bbc32-103">CDC 인스턴스 배포 스크립트를 표시하는 CDC 인스턴스 배포 스크립트 대화 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-103">The CDC Instance Deployment Script dialog box that displays the CDC instance deployment script.</span></span> <span data-ttu-id="bbc32-104">이 스크립트를 사용하여 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 모든 아티팩트를 포함하는 CDC 데이터베이스를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-104">This script can be used to re-create the CDC database with all of its artifacts on a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="bbc32-105">배포 스크립트가 완료되면 다음을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-105">At the completion of the deployment script, you should make sure of the following:</span></span>  
  
-   <span data-ttu-id="bbc32-106">배포 스크립트에서는 Oracle CDC Service 구성 콘솔 또는 프로그램에서 만들어지는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 준비 스크립트 **를 사용하여 대상** 인스턴스가 Oracle CDC에 사용할 수 있도록 준비된 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-106">The deployment script assumes that the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance was prepared for Oracle CDC, by using the Oracle CDC Service Configuration Console or by using **prepare script** that program creates.</span></span>  
  
-   <span data-ttu-id="bbc32-107">CDC에 데이터베이스를 사용하도록 설정하는 데 사용되는 스크립트 부분을 `sysadmin`이 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-107">The part of the script that is used to enable the database for CDC needs to be run by a `sysadmin`.</span></span>  
  
-   <span data-ttu-id="bbc32-108">이 스크립트는 Oracle 로그 마이닝 암호를 유지하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-108">The script does not preserve the Oracle log-mining password.</span></span> <span data-ttu-id="bbc32-109">스크립트가 실행되고 Oracle CDC Service가 시작된 후에 암호를 수동으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-109">This needs to be set manually after the script is run and the Oracle CDC Service is started.</span></span>  
  
 <span data-ttu-id="bbc32-110">**CDC 인스턴스 배포 스크립트** 대화 상자에서 다음 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-110">Select the following options in the **CDC Instance Deployment Script** dialog box.</span></span>  
  
 <span data-ttu-id="bbc32-111">**다른 이름으로 저장**</span><span class="sxs-lookup"><span data-stu-id="bbc32-111">**Save As**</span></span>  
 <span data-ttu-id="bbc32-112">원하는 위치에 저장할 수 있는 텍스트 파일로 스크립트를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-112">Saves the script in a text file that you can save in any location you want.</span></span> <span data-ttu-id="bbc32-113">스크립트를 포함하는 파일을 다른 서버에 복사하여 해당 서버에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-113">You can copy the file with the script to any other server to run it there.</span></span>  
  
 <span data-ttu-id="bbc32-114">**Copy**</span><span class="sxs-lookup"><span data-stu-id="bbc32-114">**Copy**</span></span>  
 <span data-ttu-id="bbc32-115">스크립트를 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-115">Copies the script to the clipboard.</span></span> <span data-ttu-id="bbc32-116">그런 다음 스크립트를 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 텍스트 편집기에 붙여넣어 나중에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bbc32-116">You can then paste the script into the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or any text editor to run the scripts later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc32-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bbc32-117">See Also</span></span>  
 [<span data-ttu-id="bbc32-118">CDC를 위한 SQL Server 준비</span><span class="sxs-lookup"><span data-stu-id="bbc32-118">Prepare SQL Server for CDC</span></span>](prepare-sql-server-for-cdc.md)  
  
  
