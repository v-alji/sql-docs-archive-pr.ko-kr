---
title: 자격 증명 만들기 - Azure Storage 인증 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: afdbf2647c79e07cf3f190ec6710eeb6b7718f6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740072"
---
# <a name="create-credential---authenticate-to-azure-storage"></a><span data-ttu-id="e5c58-102">자격 증명 만들기 - Azure 스토리지 인증</span><span class="sxs-lookup"><span data-stu-id="e5c58-102">Create Credential - Authenticate to Azure Storage</span></span>
  <span data-ttu-id="e5c58-103">**URL로 백업 - 자격 증명 만들기** 대화 상자를 사용하여 새 SQL 자격 증명을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-103">Use the **Backup to URL - Create Credential** dialog box to create a new SQL Credential.</span></span>  
  
 <span data-ttu-id="e5c58-104">이 대화 상자를 사용하여 자격 증명을 만들 때 로컬 인증서 저장소에 추가된 Azure 관리 인증서 또는 컴퓨터에 다운로드된 게시 프로필을 제공하여 구독 및 스토리지 계정 정보의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-104">When using this dialog box to create a credential, you must provide an Azure Management Certificate added to the local certificate store or a publishing profile downloaded to your computer to validate the subscription and the storage account information.</span></span>  
  
 <span data-ttu-id="e5c58-105">**SQL 자격 증명**</span><span class="sxs-lookup"><span data-stu-id="e5c58-105">**SQL Credential**</span></span>  
 <span data-ttu-id="e5c58-106">만들려는 SQL 자격 증명의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-106">Specify the name of the SQL Credential you want to create.</span></span>  
  
## <a name="azure-credentials"></a><span data-ttu-id="e5c58-107">Azure 자격 증명</span><span class="sxs-lookup"><span data-stu-id="e5c58-107">Azure Credentials</span></span>  
 <span data-ttu-id="e5c58-108">**관리 인증서**</span><span class="sxs-lookup"><span data-stu-id="e5c58-108">**Management Certificate**</span></span>  
 <span data-ttu-id="e5c58-109">이 옵션을 사용하여 Azure의 관리 인증서와 일치하는 로컬 인증서 저장소의 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-109">Use this option to specify a certificate from the local certificate store that matches the management certificate from Azure.</span></span> <span data-ttu-id="e5c58-110">Azure 관리 인증서에 대한 자세한 내용은 [Azure용 관리 인증서 만들기 및 업로드](https://go.microsoft.com/fwlink/?LinkId=320781)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5c58-110">For more information on Azure management certificate, see [Create and Upload a Management Certificate for Azure](https://go.microsoft.com/fwlink/?LinkId=320781).</span></span>  
  
 <span data-ttu-id="e5c58-111">**구독**</span><span class="sxs-lookup"><span data-stu-id="e5c58-111">**Subscription**</span></span>  
 <span data-ttu-id="e5c58-112">로컬 인증서 저장소의 관리 인증서와 일치하는 Azure 구독 ID를 선택, 입력 또는 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-112">Select, type, or paste your Azure subscription ID that matches the management certificate from the local certificate store.</span></span>  
  
 <span data-ttu-id="e5c58-113">**게시 프로필**</span><span class="sxs-lookup"><span data-stu-id="e5c58-113">**Publishing Profile**</span></span>  
 <span data-ttu-id="e5c58-114">게시 프로필을 컴퓨터에 다운로드한 경우 이 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-114">Use this option if you have a publishing profile downloaded to your computer.</span></span> <span data-ttu-id="e5c58-115">이 옵션을 사용하는 경우 구독 ID 및 인증서가 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-115">If you use this option, the subscription ID, and the certificate are auto populated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e5c58-116">SQL Server는 현재 프로필 버전 2.0 게시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-116">SQL Server currently supports publishing profile version 2.0.</span></span> <span data-ttu-id="e5c58-117">게시 프로필의 지원되는 버전을 다운로드하려면 [게시 프로필 2.0 다운로드](https://go.microsoft.com/fwlink/?LinkId=396421)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5c58-117">To download the supported version of the publishing profile, see [Download Publishing Profile 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).</span></span>  
  
## <a name="storage-account"></a><span data-ttu-id="e5c58-118">스토리지 계정</span><span class="sxs-lookup"><span data-stu-id="e5c58-118">Storage Account</span></span>  
 <span data-ttu-id="e5c58-119">백업 파일을 저장하는 데 사용할 스토리지 계정을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5c58-119">Select the storage account you want to use to store the backup files on.</span></span>  
  
  
