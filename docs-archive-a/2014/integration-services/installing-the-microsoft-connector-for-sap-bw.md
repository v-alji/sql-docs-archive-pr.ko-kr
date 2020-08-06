---
title: 1.1 SAP BW 용 Microsoft Connector 설치 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3bfb9023-9597-4f59-9085-4b9057e7702e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0ef96f38054f04e71de72bda0bbb12f8f003ef20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650181"
---
# <a name="installing-the-microsoft-connector-for-11-sap-bw"></a><span data-ttu-id="ab11c-102">Microsoft Connector for 1.1 SAP BW 설치</span><span class="sxs-lookup"><span data-stu-id="ab11c-102">Installing the Microsoft Connector for 1.1 SAP BW</span></span>
  <span data-ttu-id="ab11c-103">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 및 해당 설명서를 설치하려면 SQL Server 기능 팩 웹 페이지에서 Windows Installer 패키지를 다운로드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-103">To install the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW and its documentation, download and run the Windows installer package from the SQL Server Feature Pack Web page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ab11c-104">SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-104">The documentation for the Microsoft Connector 1.1 for SAP BW assumes familiarity with the SAP Netweaver BW environment.</span></span> <span data-ttu-id="ab11c-105">SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab11c-105">For more information about SAP Netweaver BW, or for information about how to configure SAP Netweaver BW objects and processes, see your SAP documentation.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="ab11c-106">SAP Netweaver BW에서 데이터를 추출하려면 추가 SAP 라이선스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-106">Extracting data from SAP Netweaver BW requires additional SAP licensing.</span></span> <span data-ttu-id="ab11c-107">SAP에서 이러한 요구 사항을 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab11c-107">Check with SAP to verify these requirements.</span></span>  
  
## <a name="required-sap-files"></a><span data-ttu-id="ab11c-108">필요한 SAP 파일</span><span class="sxs-lookup"><span data-stu-id="ab11c-108">Required SAP Files</span></span>  
 <span data-ttu-id="ab11c-109">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1을 사용하기 위해서는 로컬 컴퓨터에 SAP Front End 소프트웨어(SAP GUI)를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-109">To use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW, you do not have to install the SAP Front End software (SAP GUI) on the local computer.</span></span>  
  
 <span data-ttu-id="ab11c-110">하지만 SAP .NET 커넥터 파일 librfc32.dll을 Windows 폴더의 system 하위 폴더에 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-110">However you must copy the SAP .NET connector file, librfc32.dll, into the system subfolder in the Windows folder.</span></span> <span data-ttu-id="ab11c-111">일반적으로 이 폴더 위치는 **C:\Windows\system32**입니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-111">(Typically, this folder location is **C:\Windows\system32**.)</span></span>  
  
## <a name="considerations-for-64-bit-computers"></a><span data-ttu-id="ab11c-112">64비트 컴퓨터에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="ab11c-112">Considerations for 64-bit Computers</span></span>  
 <span data-ttu-id="ab11c-113">SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1은 64비트 버전의 [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows를 완전히 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-113">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW fully supports the 64-bit version of [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows.</span></span> <span data-ttu-id="ab11c-114">64비트 컴퓨터에서 SAP BW용 [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1은 다음과 같은 추가 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-114">On a 64-bit computer, the [!INCLUDE[msCoName](../includes/msconame-md.md)] Connector 1.1 for SAP BW has the following additional requirements:</span></span>  
  
-   <span data-ttu-id="ab11c-115">64비트 Windows 운영 체제에서 패키지를 64비트 모드로 실행하려면 SAP GUI 파일 librfc32.dll의 64비트 버전을 Windows 폴더의 **system32** 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-115">To run packages in 64-bit mode on any 64-bit Windows operating system, copy the 64-bit version of the SAP GUI file, librfc32.dll, into the **system32** folder of the Windows folder.</span></span> <span data-ttu-id="ab11c-116">일반적으로 이 파일 위치는 **C:\Windows\system32**입니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-116">(Typically, this file location is **C:\Windows\system32**.)</span></span>  
  
-   <span data-ttu-id="ab11c-117">64비트 Windows 운영 체제에서 패키지를 32비트 모드로 실행하려면 SAP GUI 파일 librfc32.dll을 Windows 폴더의 **SysWow64** 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-117">To run packages in 32-bit mode on any 64-bit Windows operating system, copy the SAP GUI file, librfc32.dll, into the **SysWow64** folder of the Windows folder.</span></span> <span data-ttu-id="ab11c-118">일반적으로 이 폴더 위치는 **C:\Windows\SysWow64**입니다.</span><span class="sxs-lookup"><span data-stu-id="ab11c-118">(Typically, this folder location is **C:\Windows\SysWow64**.)</span></span>  
  
  
